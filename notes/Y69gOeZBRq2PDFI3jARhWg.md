老鼠走迷宮
<pre>

	private: String^ originalMazeText;
	private: System::Void tabPage1_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	
    
	private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e) {
		
		originalMazeText = richTextBox1->Text;
		String^ mazeText = richTextBox1->Text;
		array<String^>^ lines = mazeText->Split('\n');
		

		int number;
		String^ input = textBox1->Text->Trim();
		
		int height = 0;
		int width = 0;
		for each (String ^ line in lines) {
			if (!String::IsNullOrWhiteSpace(line)) {
				height++;
				if (height == 1) {
					array<String^>^ cells = line->Split(' ');
					width = cells->Length;
				}
			}
		}

		// Create the maze array
		array<array<int>^>^ maze = gcnew array<array<int>^>(height);
		int entranceX = -1, entranceY = -1;
		int exitX = -1, exitY = -1;

		for (int i = 0; i < height; i++) {
			maze[i] = gcnew array<int>(width);
			if (i < lines->Length) {
				array<String^>^ cells = lines[i]->Split(' ');
				for (int j = 0; j < width && j < cells->Length; j++) {
					String^ cell = cells[j]->Trim();
					if (cell == "E") {
						maze[i][j] = 0; // Mark entrance as path
						entranceX = i;
						entranceY = j;
					}
					else if (cell == "X") {
						maze[i][j] = 0; // Mark exit as path
						exitX = i;
						exitY = j;
					}
					else {
						maze[i][j] = Convert::ToInt32(cell);
					}
				}
			}
		}

		// If entrance or exit not found, use the first and last path cells
		if (entranceX == -1 || entranceY == -1) {
			for (int i = 0; i < height; i++) {
				for (int j = 0; j < width; j++) {
					if (maze[i][j] == 0) {
						entranceX = i;
						entranceY = j;
						break;
					}
				}
				if (entranceX != -1) break;
			}
		}

		if (exitX == -1 || exitY == -1) {
			for (int i = height - 1; i >= 0; i--) {
				for (int j = width - 1; j >= 0; j--) {
					if (maze[i][j] == 0) {
						exitX = i;
						exitY = j;
						break;
					}
				}
				if (exitX != -1) break;
			}
		}

		// Debug: Print entrance and exit positions
		richTextBox1->AppendText("\n入口位置: (" + entranceX + ", " + entranceY + ")");
		richTextBox1->AppendText("\n出口位置: (" + exitX + ", " + exitY + ")");

		InitializeGrid(height, width);

		// Create a solution array to track the path (0 = unvisited, 1 = visited, 2 = path)
		array<array<int>^>^ solution = gcnew array<array<int>^>(height);
		for (int i = 0; i < height; i++) {
			solution[i] = gcnew array<int>(width);
			for (int j = 0; j < width; j++) {
				solution[i][j] = 0;
			}
		}

		// Solve using recursive backtracking
		bool solved = SolveMazeUtilview(maze, solution, entranceX, entranceY, exitX, exitY);

		// Display the result
		if (solved) {
			// Create a string representation of the solution
			String^ solutionStr = "";
			for (int i = 0; i < height; i++) {
				for (int j = 0; j < width; j++) {
					if (i == entranceX && j == entranceY) {
						solutionStr += "E ";
					}
					else if (i == exitX && j == exitY) {
						solutionStr += "X ";
					}
					else if (solution[i][j] == 2) {
						solutionStr += "P "; // Path
					}
					else if (maze[i][j] == 1) {
						solutionStr += "1 "; // Wall
					}
					else {
						solutionStr += "0 "; // Open space
					}
				}
				solutionStr += "\n";
			}

			richTextBox1->Text = solutionStr;
			richTextBox1->AppendText("\n迷宮解決方案找到！");
		}
		else {
			richTextBox1->AppendText("\n無法找到解決方案！");
		}
	}
	
	private: System::Void MyForm_Load(System::Object^ sender, System::EventArgs^ e) {
		this->button6->Click += gcnew System::EventHandler(this, &MyForm::button6_Click);
	}
	
	

	private: bool SolveMazeUtil(array<array<int>^>^ maze, array<array<int>^>^ solution, int x, int y, int exitX, int exitY) {
		// Check if the cell is out of bounds or not walkable
		if (x < 0 || x >= maze->Length || y < 0 || y >= maze[0]->Length || maze[x][y] != 0 || solution[x][y] != 0) {
			return false;
		}

		// If we reach the exit, mark and return success
		if (x == exitX && y == exitY) {
			solution[x][y] = 2;
			return true;
		}

		// Mark this cell as visited (temporarily)
		solution[x][y] = 1;

		// Define movement directions: Right, Down, Left, Up
		array<int>^ dx = { 0, 1, 0, -1 };
		array<int>^ dy = { 1, 0, -1, 0 };

		array<int>^ randomOrder = { 0, 1, 2, 3 };
		Random^ rand = gcnew Random();
		for (int i = 0; i < 4; i++) {
			int swapIndex = rand->Next(4);
			int temp = randomOrder[i];
			randomOrder[i] = randomOrder[swapIndex];
			randomOrder[swapIndex] = temp;
		}

		// Try each direction
		for (int i = 0; i < 4; i++) {
			int nextX = x + dx[i];
			int nextY = y + dy[i];

			// Recursive call to explore further
			if (SolveMazeUtil(maze, solution, nextX, nextY, exitX, exitY)) {
				solution[x][y] = 2; // Mark part of the valid path
				return true;
			}
		}

		// Backtrack if all directions fail
		solution[x][y] = 0;
		return false;
	
	}

	private: System::Void button2_Click(System::Object^ sender, System::EventArgs^ e) {
		//RandomSolveMaze();  // 使用隨機路徑尋找解法
		richTextBox1->Clear();
		richTextBox1->Text = originalMazeText;
		
		// Parse the current maze from richTextBox1
		String^ mazeText = richTextBox1->Text;
		array<String^>^ lines = mazeText->Split('\n');


		// Find the dimensions
		int height = 0;
		int width = 0;
		for each (String ^ line in lines) {
			if (!String::IsNullOrWhiteSpace(line)) {
				height++;
				if (height == 1) {
					array<String^>^ cells = line->Split(' ');
					width = cells->Length;
				}
			}
		}

		// Create the maze array
		array<array<int>^>^ maze = gcnew array<array<int>^>(height);
		int entranceX = -1, entranceY = -1;
		int exitX = -1, exitY = -1;

		for (int i = 0; i < height; i++) {
			maze[i] = gcnew array<int>(width);
			if (i < lines->Length) {
				array<String^>^ cells = lines[i]->Split(' ');
				for (int j = 0; j < width && j < cells->Length; j++) {
					String^ cell = cells[j]->Trim();
					if (cell == "E") {
						maze[i][j] = 0; // Mark entrance as path
						entranceX = i;
						entranceY = j;
					}
					else if (cell == "X") {
						maze[i][j] = 0; // Mark exit as path
						exitX = i;
						exitY = j;
					}
					else {
						maze[i][j] = Convert::ToInt32(cell);
					}
				}
			}
		}

		// If entrance or exit not found, use the first and last path cells
		if (entranceX == -1 || entranceY == -1) {
			for (int i = 0; i < height; i++) {
				for (int j = 0; j < width; j++) {
					if (maze[i][j] == 0) {
						entranceX = i;
						entranceY = j;
						break;
					}
				}
				if (entranceX != -1) break;
			}
		}

		if (exitX == -1 || exitY == -1) {
			for (int i = height - 1; i >= 0; i--) {
				for (int j = width - 1; j >= 0; j--) {
					if (maze[i][j] == 0) {
						exitX = i;
						exitY = j;
						break;
					}
				}
				if (exitX != -1) break;
			}
		}

		// Create a solution array
		array<array<int>^>^ solution = gcnew array<array<int>^>(height);
		for (int i = 0; i < height; i++) {
			solution[i] = gcnew array<int>(width);
			for (int j = 0; j < width; j++) {
				solution[i][j] = 0;
			}
		}

		// Random walk
		Random^ rand = gcnew Random();
		int x = entranceX;
		int y = entranceY;
		solution[x][y] = 2; // Mark as part of the path

		
		System::Collections::Generic::Stack<System::Drawing::Point>^ pathStack = gcnew System::Collections::Generic::Stack<System::Drawing::Point>();
		pathStack->Push(System::Drawing::Point(x, y));

		// Define movement directions: up, right, down, left
		array<int>^ dx = { -1, 0, 1, 0 };
		array<int>^ dy = { 0, 1, 0, -1 };

		while (pathStack->Count > 0 && !(x == exitX && y == exitY)) {
			// Get available moves
			List<int>^ availableMoves = gcnew List<int>();

			for (int i = 0; i < 4; i++) {
				int nextX = x + dx[i];
				int nextY = y + dy[i];

				if (nextX >= 0 && nextX < height && nextY >= 0 && nextY < width &&
					maze[nextX][nextY] == 0 && solution[nextX][nextY] == 0) {
					availableMoves->Add(i);
				}
			}

			if (availableMoves->Count > 0) {
				// Randomly choose a direction
				int moveIndex = rand->Next(availableMoves->Count);
				int direction = availableMoves[moveIndex];

				x += dx[direction];
				y += dy[direction];

				solution[x][y] = 2; // Mark as part of the path
				pathStack->Push(Point(x, y));
			}
			else {
				// Backtrack
				pathStack->Pop();
				if (pathStack->Count > 0) {
					Point p = pathStack->Peek();
					x = p.X;
					y = p.Y;
				}
			}
		}

		// Display the result
		if (x == exitX && y == exitY) {
			// Create a string representation of the solution
			String^ solutionStr = "";
			for (int i = 0; i < height; i++) {
				for (int j = 0; j < width; j++) {
					if (i == entranceX && j == entranceY) {
						solutionStr += "E ";
					}
					else if (i == exitX && j == exitY) {
						solutionStr += "X ";
					}
					else if (solution[i][j] == 2) {
						solutionStr += "P "; // Path
					}
					else if (maze[i][j] == 1) {
						solutionStr += "1 "; // Wall
					}
					else {
						solutionStr += "0 "; // Open space
					}
				}
				solutionStr += "\n";
			}

			richTextBox1->Text = solutionStr;
			richTextBox1->AppendText("\n隨機迷宮解決方案找到！");
		}
		else {
			richTextBox1->AppendText("\n無法找到隨機解決方案！");
		}
		
	}
	private: System::Void button3_Click(System::Object^ sender, System::EventArgs^ e) {
		String^ mazeContent = this->richTextBox1->Text;
		System::IO::File::WriteAllText("maze.txt", mazeContent);
		this->richTextBox1->AppendText("\n迷宮已保存到 maze.txt");
	}

	private: int currentFileIndex = 0;
	//private: array<String^>^ mazeFiles = gcnew array<String^> { "maze.txt", "maze1.txt", "maze2.txt", "maze3.txt" };

	private: System::Void button4_Click(System::Object^ sender, System::EventArgs^ e) {
		richTextBox1->Clear();
		// 讀取三個迷宮文件
		array<String^>^ mazeFiles = gcnew array<String^> { "maze.txt", "maze1.txt", "maze2.txt","maze3.txt" };

		if (currentFileIndex < mazeFiles->Length) {
			String^ file = mazeFiles[currentFileIndex];
			if (System::IO::File::Exists(file)) {
				String^ mazeContent = System::IO::File::ReadAllText(file);
				this->richTextBox1->AppendText(mazeContent);
			}
			currentFileIndex++;
		}
		else {
			this->richTextBox1->AppendText("\n所有文件已加載完畢");
			currentFileIndex = 0; // 重置索引以便重新開始
		}
	}
	
	private: System::Void button6_Click(System::Object^ sender, System::EventArgs^ e) {
		int height = Convert::ToInt32(this->textBox1->Text);
		int width = Convert::ToInt32(this->textBox2->Text);
		String^ entrance = this->textBox4->Text;
		String^ exit = this->textBox3->Text;


		//List<Point>^ frontier = gcnew List<Point>();

		// 
		String^ maze = GeneratePrimMaze(height, width, entrance, exit);
		this->richTextBox1->Text = maze;
		//this->richTextBox1->AppendText("\n迷宮2生成完成");

		 // 將迷宮數據加載到 DataGridView 中
		//LoadMazeToDataGridView(maze, height, width);
		String^ input = richTextBox1->Text;

		array<String^>^ rows = input->Split('\n');
		int rowCount = rows->Length;
		int colCount = rows[0]->Split(' ')->Length;

		dataGridView1->RowCount = rowCount;
		dataGridView1->ColumnCount = colCount;

		// 設置每個格子的大小
		for (int i = 0; i < colCount; i++) {
			dataGridView1->Columns[i]->Width = 30;
		}
		for (int i = 0; i < rowCount; i++) {
			dataGridView1->Rows[i]->Height = 30;
		}

		
		for (int i = 0; i < rowCount; i++) {
			array<String^>^ cells = rows[i]->Trim()->Split(' ');

			for (int j = 0; j < colCount; j++) {
				dataGridView1->Rows[i]->Cells[j]->Value = cells[j];

				if (cells[j] == "1") {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::Black; // 障礙物
				}
				else if (cells[j] == "0") {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::White; // 道路
				}
				else if (cells[j] == "S") {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::Green; // 起點
				}
				else if (cells[j] == "E") {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::Red; // 終點
				}
			}
		}
	}
	
		// 基於隨機 Prim 算法的迷宮生成
		String^ GeneratePrimMaze(int height, int width, String^ entrance, String^ exit) {
			// 初始化迷宮，所有單元格都為牆（1）
			array<array<int>^>^ maze = gcnew array<array<int>^>(height);
			for (int i = 0; i < height; i++) {
				maze[i] = gcnew array<int>(width);
				for (int j = 0; j < width; j++) {
					maze[i][j] = 1; // 1 代表牆
				}
			}

			// 解析入口和出口座標
			array<String^>^ entranceCoords = entrance->Split(',');
			int entranceX = Convert::ToInt32(entranceCoords[0]->Trim());
			int entranceY = Convert::ToInt32(entranceCoords[1]->Trim());

			array<String^>^ exitCoords = exit->Split(',');
			int exitX = Convert::ToInt32(exitCoords[0]->Trim());
			int exitY = Convert::ToInt32(exitCoords[1]->Trim());

			// 確保入口和出口在迷宮範圍內
			if (entranceX < 0 || entranceX >= height || entranceY < 0 || entranceY >= width ||
				exitX < 0 || exitX >= height || exitY < 0 || exitY >= width) {
				return "錯誤：入口或出口座標超出迷宮範圍！";
			}

			// 將入口和出口標記為路
			maze[entranceX][entranceY] = 0; // 0 代表路
			maze[exitX][exitY] = 0;

			// 隨機選擇一個起始點
			Random^ rand = gcnew Random();
			int startX = entranceX; // 從入口開始
			int startY = entranceY;

			// 初始化邊界列表
			List<Point>^ frontier = gcnew List<Point>();
			AddFrontier(maze, frontier, startX, startY, height, width);

			// 使用 Prim 算法生成迷宮
			while (frontier->Count > 0) {
				int index = rand->Next(frontier->Count);
				Point p = frontier[index];
				frontier->RemoveAt(index);

				// 檢查是否可以打通
				if (maze[p.X][p.Y] == 1) {
					maze[p.X][p.Y] = 0; // 打通目標單元格
					ConnectToMaze(maze, p.X, p.Y, rand, height, width);
					AddFrontier(maze, frontier, p.X, p.Y, height, width);
				}
			}
			EnsureExitHasAdjacentPath(maze, exitX, exitY, height, width, rand);


			// 將迷宮轉換為字串
			String^ mazeStr = "";
			for (int i = 0; i < height; i++) {
				for (int j = 0; j < width; j++) {
					if (i == entranceX && j == entranceY) {
						mazeStr += "E "; // 標記入口
					}
					else if (i == exitX && j == exitY) {
						mazeStr += "X "; // 標記出口
					}
					else {
						mazeStr += maze[i][j] == 1 ? "1 " : "0 ";
					}
				}
				mazeStr = mazeStr->TrimEnd(); // 去掉每行末尾的空格
				mazeStr += "\n";
			}

			return mazeStr->TrimEnd(); // 去掉最後一行的換行符


		}

		// 添加邊界單元格
		void AddFrontier(array<array<int>^>^ maze, List<Point>^ frontier, int x, int y, int height, int width) {
			array<int>^ dx = { -1, 1, 0, 0 };
			array<int>^ dy = { 0, 0, -1, 1 };

			for (int i = 0; i < 4; i++) {
				int nx = x + dx[i] * 2;
				int ny = y + dy[i] * 2;

				// 檢查是否在範圍內且為牆
				if (nx >= 0 && nx < height && ny >= 0 && ny < width && maze[nx][ny] == 1) {
					frontier->Add(Point(nx, ny));
				}
			}
		}

		// 連接到迷宮
		void ConnectToMaze(array<array<int>^>^ maze, int x, int y, Random^ rand, int height, int width) {
			array<int>^ dx = { -2, 2, 0, 0 };
			array<int>^ dy = { 0, 0, -2, 2 };
			array<int>^ directions = { 0, 1, 2, 3 };
			Shuffle(directions, rand);

			for (int i = 0; i < 4; i++) {
				int nx = x + dx[directions[i]];
				int ny = y + dy[directions[i]];

				// 檢查是否在範圍內且為路
				if (nx >= 0 && nx < height && ny >= 0 && ny < width && maze[nx][ny] == 0) {
					// 打通中間的牆
					int wallX = (x + nx) / 2;
					int wallY = (y + ny) / 2;
					maze[wallX][wallY] = 0;
					break;
				}
			}
		}

		// 隨機打亂陣列
		void Shuffle(array<int>^ array, Random^ rand) {
			for (int i = array->Length - 1; i > 0; i--) {
				int j = rand->Next(i + 1);
				int temp = array[i];
				array[i] = array[j];
				array[j] = temp;
			}
			
		}

		void EnsureExitHasAdjacentPath(array<array<int>^>^ maze, int exitX, int exitY, int height, int width, Random^ rand) {
			array<int>^ dx = { -1, 1, 0, 0 };
			array<int>^ dy = { 0, 0, -1, 1 };

			bool hasAdjacentPath = false;
			for (int i = 0; i < 4; i++) {
				int nx = exitX + dx[i];
				int ny = exitY + dy[i];

				if (nx >= 0 && nx < height && ny >= 0 && ny < width && maze[nx][ny] == 0) {
					hasAdjacentPath = true;
					break;
				}
			}

			if (!hasAdjacentPath) {
				int direction = rand->Next(4);
				int nx = exitX + dx[direction];
				int ny = exitY + dy[direction];

				if (nx >= 0 && nx < height && ny >= 0 && ny < width) {
					maze[nx][ny] = 0;
				}
			}
		}
	

	private: void InitializeGrid(int rows, int cols) {
		dataGridView1->RowCount = rows;
		dataGridView1->ColumnCount = cols;

		// Set cell size
		for (int i = 0; i < cols; i++) {
			dataGridView1->Columns[i]->Width = 30;
		}
		for (int i = 0; i < rows; i++) {
			dataGridView1->Rows[i]->Height = 30;
		}
		for (int i = 0; i < rows; i++) {
			for (int j = 0; j < cols; j++) {
				dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::White;
			}
		}
	}

	private: void UpdateMazeDisplay(array<array<int>^>^ maze, array<array<int>^>^ solution, int mouseX, int mouseY) {
		// Add this at the beginning of the UpdateMazeDisplay method to ensure UI updates are visible
		Application::DoEvents();
		System::Threading::Thread::Sleep(100); // Adjust delay as needed

		for (int i = 0; i < maze->Length; i++) {
			for (int j = 0; j < maze[0]->Length; j++) {
				if (i == mouseX && j == mouseY) {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::Red; // Mouse position
				}
				else if (solution[i][j] == 2) {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::LightGreen; // Correct path
				}
				else if (maze[i][j] == 1) {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::Black; // Walls
				}
				else {
					dataGridView1->Rows[i]->Cells[j]->Style->BackColor = System::Drawing::Color::White; // Empty space
				}
			}
		}

		// Force UI refresh to show changes immediately
		//Application::DoEvents();
		//System::Threading::Thread::Sleep(200); // Delay for visual effect
	}

	private: bool SolveMazeUtilview(array<array<int>^>^ maze, array<array<int>^>^ solution, int x, int y, int exitX, int exitY) {
		// Boundary checks & invalid moves
		if (x < 0 || x >= maze->Length || y < 0 || y >= maze[0]->Length || maze[x][y] != 0 || solution[x][y] != 0) {
			return false;
		}

		// Mark this cell as part of the path
		solution[x][y] = 1;

		// Update the DataGridView to reflect the current state
		UpdateMazeDisplay(maze, solution, x, y);

		// If we reached the exit
		if (x == exitX && y == exitY) {
			solution[x][y] = 2;
			return true;
		}

		// Move directions (right, down, left, up)
		array<int>^ dx = { 0, 1, 0, -1 };
		array<int>^ dy = { 1, 0, -1, 0 };

		for (int i = 0; i < 4; i++) {
			int nextX = x + dx[i];
			int nextY = y + dy[i];

			if (SolveMazeUtilview(maze, solution, nextX, nextY, exitX, exitY)) {
				solution[x][y] = 2; // Mark correct path
				return true;
			}
		}

		// Backtrack
		solution[x][y] = 0;
		UpdateMazeDisplay(maze, solution, x, y); // Show backtrack step
		return false;
	}


	private: System::Void btnStart_Click(System::Object^ sender, System::EventArgs^ e) {
		int rows = 10;
		int cols = 10;

		array<array<int>^>^ maze = gcnew array<array<int>^>(rows);
		array<array<int>^>^ solution = gcnew array<array<int>^>(rows);

		// Example maze setup (1 = wall, 0 = open path)
		for (int i = 0; i < rows; i++) {
			maze[i] = gcnew array<int>(cols);
			solution[i] = gcnew array<int>(cols);
			for (int j = 0; j < cols; j++) {
				maze[i][j] = (rand() % 4 == 0) ? 1 : 0; // Random walls
			}
		}

		// Set start and exit positions
		int startX = 0, startY = 0;
		int exitX = rows - 1, exitY = cols - 1;
		maze[startX][startY] = 0;
		maze[exitX][exitY] = 0;

		InitializeGrid(rows, cols);
		UpdateMazeDisplay(maze, solution, startX, startY);

		// Start solving
		if (SolveMazeUtilview(maze, solution, startX, startY, exitX, exitY)) {
			MessageBox::Show("Maze solved!", "Success");
		}
		else {
			MessageBox::Show("No solution found.", "Failed");
		}
	}


	private: System::Void trackBar1_Scroll(System::Object^ sender, System::EventArgs^ e) {
		int speed = trackBar1->Value;
			// 假設 `SetAnimationSpeed(int speed)` 來設定動畫速度
		float animationDelay = 1000 / speed;
	}
</pre>