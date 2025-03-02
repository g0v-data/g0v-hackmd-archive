# data structure hw1
<pre>
#pragma once
#include <ctime> //cpu time
#include <chrono>


namespace CppCLRWinFormsProject {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;

	public ref class Form1 : public System::Windows::Forms::Form
	{
	public:
		Form1(void)
		{
			InitializeComponent();
		}

	protected:
		~Form1()
		{
			if (components)
			{
				delete components;
			}
		}

	private:
		System::Windows::Forms::Button^ button1;
		System::Windows::Forms::TextBox^ textBox1;

		System::Windows::Forms::Label^ label1;
	private: System::Windows::Forms::Label^ label2;
	private: System::Windows::Forms::TextBox^ textBox2;
	private: System::Windows::Forms::Button^ button2;
	private: System::Windows::Forms::RichTextBox^ richTextBox2;

	private: System::Windows::Forms::Button^ button3;
	private: System::Windows::Forms::Button^ button4;
	private: System::Windows::Forms::RichTextBox^ richTextBox3;
	private: System::Windows::Forms::RichTextBox^ richTextBox4;
	private: System::Windows::Forms::CheckBox^ checkBox1;
	private: System::Windows::Forms::CheckBox^ checkBox2;
	private: System::Windows::Forms::TextBox^ textBox3;
	private: System::Windows::Forms::Label^ label3;
	private: System::Windows::Forms::Label^ label4;
	private: System::Windows::Forms::TextBox^ textBox4;
	private: System::Windows::Forms::Button^ button5;
	private: System::Windows::Forms::RichTextBox^ richTextBox5;
	private: System::Windows::Forms::TextBox^ textBox5;
	private: System::Windows::Forms::Label^ label5;

	private: System::Windows::Forms::RichTextBox^ richTextBox1;
		   System::ComponentModel::Container^ components;

#pragma region Windows Form Designer generated code
		   void InitializeComponent(void)
		   {
			   this->button1 = (gcnew System::Windows::Forms::Button());
			   this->textBox1 = (gcnew System::Windows::Forms::TextBox());
			   this->label1 = (gcnew System::Windows::Forms::Label());
			   this->label2 = (gcnew System::Windows::Forms::Label());
			   this->textBox2 = (gcnew System::Windows::Forms::TextBox());
			   this->button2 = (gcnew System::Windows::Forms::Button());
			   this->richTextBox2 = (gcnew System::Windows::Forms::RichTextBox());
			   this->button3 = (gcnew System::Windows::Forms::Button());
			   this->button4 = (gcnew System::Windows::Forms::Button());
			   this->richTextBox3 = (gcnew System::Windows::Forms::RichTextBox());
			   this->richTextBox4 = (gcnew System::Windows::Forms::RichTextBox());
			   this->checkBox1 = (gcnew System::Windows::Forms::CheckBox());
			   this->checkBox2 = (gcnew System::Windows::Forms::CheckBox());
			   this->textBox3 = (gcnew System::Windows::Forms::TextBox());
			   this->label3 = (gcnew System::Windows::Forms::Label());
			   this->label4 = (gcnew System::Windows::Forms::Label());
			   this->textBox4 = (gcnew System::Windows::Forms::TextBox());
			   this->button5 = (gcnew System::Windows::Forms::Button());
			   this->richTextBox5 = (gcnew System::Windows::Forms::RichTextBox());
			   this->textBox5 = (gcnew System::Windows::Forms::TextBox());
			   this->label5 = (gcnew System::Windows::Forms::Label());
			   this->richTextBox1 = (gcnew System::Windows::Forms::RichTextBox());
			   this->SuspendLayout();
			   // 
			   // button1
			   // 
			   this->button1->BackColor = System::Drawing::SystemColors::Info;
			   this->button1->Font = (gcnew System::Drawing::Font(L"新細明體", 9, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				   static_cast<System::Byte>(136)));
			   this->button1->Location = System::Drawing::Point(84, 109);
			   this->button1->Name = L"button1";
			   this->button1->Size = System::Drawing::Size(233, 54);
			   this->button1->TabIndex = 0;
			   this->button1->Text = L"generate random number";
			   this->button1->UseVisualStyleBackColor = false;
			   this->button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
			   // 
			   // textBox1
			   // 
			   this->textBox1->Location = System::Drawing::Point(90, 20);
			   this->textBox1->Name = L"textBox1";
			   this->textBox1->Size = System::Drawing::Size(227, 29);
			   this->textBox1->TabIndex = 1;
			   this->textBox1->Text = L"10";
			   // 
			   // label1
			   // 
			   this->label1->AutoSize = true;
			   this->label1->Location = System::Drawing::Point(42, 20);
			   this->label1->Name = L"label1";
			   this->label1->Size = System::Drawing::Size(36, 18);
			   this->label1->TabIndex = 3;
			   this->label1->Text = L"n = ";
			   // 
			   // label2
			   // 
			   this->label2->AutoSize = true;
			   this->label2->Location = System::Drawing::Point(12, 58);
			   this->label2->Name = L"label2";
			   this->label2->Size = System::Drawing::Size(66, 18);
			   this->label2->TabIndex = 4;
			   this->label2->Text = L"range = ";
			   // 
			   // textBox2
			   // 
			   this->textBox2->Location = System::Drawing::Point(90, 58);
			   this->textBox2->Name = L"textBox2";
			   this->textBox2->Size = System::Drawing::Size(227, 29);
			   this->textBox2->TabIndex = 5;
			   this->textBox2->Text = L"109866";
			   // 
			   // button2
			   // 
			   this->button2->BackColor = System::Drawing::SystemColors::MenuHighlight;
			   this->button2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			   this->button2->Font = (gcnew System::Drawing::Font(L"新細明體", 12, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				   static_cast<System::Byte>(136)));
			   this->button2->ForeColor = System::Drawing::SystemColors::Control;
			   this->button2->Location = System::Drawing::Point(361, 109);
			   this->button2->Name = L"button2";
			   this->button2->Size = System::Drawing::Size(233, 54);
			   this->button2->TabIndex = 6;
			   this->button2->Text = L"selection sort";
			   this->button2->UseVisualStyleBackColor = false;
			   this->button2->Click += gcnew System::EventHandler(this, &Form1::button2_Click);
			   // 
			   // richTextBox2
			   // 
			   this->richTextBox2->Location = System::Drawing::Point(361, 199);
			   this->richTextBox2->Name = L"richTextBox2";
			   this->richTextBox2->Size = System::Drawing::Size(233, 140);
			   this->richTextBox2->TabIndex = 7;
			   this->richTextBox2->Text = L"";
			   // 
			   // button3
			   // 
			   this->button3->BackColor = System::Drawing::Color::LightSalmon;
			   this->button3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::None;
			   this->button3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			   this->button3->Font = (gcnew System::Drawing::Font(L"新細明體", 12, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				   static_cast<System::Byte>(136)));
			   this->button3->ForeColor = System::Drawing::SystemColors::Control;
			   this->button3->Location = System::Drawing::Point(639, 109);
			   this->button3->Name = L"button3";
			   this->button3->Size = System::Drawing::Size(233, 54);
			   this->button3->TabIndex = 8;
			   this->button3->Text = L"bubble sort";
			   this->button3->UseVisualStyleBackColor = false;
			   this->button3->Click += gcnew System::EventHandler(this, &Form1::button3_Click);
			   // 
			   // button4
			   // 
			   this->button4->BackColor = System::Drawing::Color::Fuchsia;
			   this->button4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			   this->button4->Font = (gcnew System::Drawing::Font(L"新細明體", 12, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				   static_cast<System::Byte>(136)));
			   this->button4->ForeColor = System::Drawing::SystemColors::Control;
			   this->button4->Location = System::Drawing::Point(1168, 109);
			   this->button4->Name = L"button4";
			   this->button4->Size = System::Drawing::Size(233, 54);
			   this->button4->TabIndex = 9;
			   this->button4->Text = L"binary search";
			   this->button4->UseVisualStyleBackColor = false;
			   this->button4->Click += gcnew System::EventHandler(this, &Form1::button4_Click);
			   // 
			   // richTextBox3
			   // 
			   this->richTextBox3->Location = System::Drawing::Point(639, 199);
			   this->richTextBox3->Name = L"richTextBox3";
			   this->richTextBox3->Size = System::Drawing::Size(233, 140);
			   this->richTextBox3->TabIndex = 10;
			   this->richTextBox3->Text = L"";
			   // 
			   // richTextBox4
			   // 
			   this->richTextBox4->Location = System::Drawing::Point(1168, 199);
			   this->richTextBox4->Name = L"richTextBox4";
			   this->richTextBox4->Size = System::Drawing::Size(233, 140);
			   this->richTextBox4->TabIndex = 11;
			   this->richTextBox4->Text = L"";
			   // 
			   // checkBox1
			   // 
			   this->checkBox1->AutoSize = true;
			   this->checkBox1->Location = System::Drawing::Point(361, 20);
			   this->checkBox1->Name = L"checkBox1";
			   this->checkBox1->Size = System::Drawing::Size(103, 22);
			   this->checkBox1->TabIndex = 12;
			   this->checkBox1->Text = L"echo print";
			   this->checkBox1->UseVisualStyleBackColor = true;
			   // 
			   // checkBox2
			   // 
			   this->checkBox2->AutoSize = true;
			   this->checkBox2->Location = System::Drawing::Point(361, 53);
			   this->checkBox2->Name = L"checkBox2";
			   this->checkBox2->Size = System::Drawing::Size(105, 22);
			   this->checkBox2->TabIndex = 13;
			   this->checkBox2->Text = L"self check";
			   this->checkBox2->UseVisualStyleBackColor = true;
			   // 
			   // textBox3
			   // 
			   this->textBox3->Location = System::Drawing::Point(1168, 53);
			   this->textBox3->Name = L"textBox3";
			   this->textBox3->Size = System::Drawing::Size(227, 29);
			   this->textBox3->TabIndex = 14;
			   this->textBox3->Text = L"7";
			   // 
			   // label3
			   // 
			   this->label3->AutoSize = true;
			   this->label3->Location = System::Drawing::Point(1099, 55);
			   this->label3->Name = L"label3";
			   this->label3->Size = System::Drawing::Size(63, 18);
			   this->label3->TabIndex = 15;
			   this->label3->Text = L"target =";
			   // 
			   // label4
			   // 
			   this->label4->AutoSize = true;
			   this->label4->Location = System::Drawing::Point(561, 53);
			   this->label4->Name = L"label4";
			   this->label4->Size = System::Drawing::Size(89, 18);
			   this->label4->TabIndex = 16;
			   this->label4->Text = L"repetition =";
			   // 
			   // textBox4
			   // 
			   this->textBox4->Location = System::Drawing::Point(666, 51);
			   this->textBox4->Name = L"textBox4";
			   this->textBox4->Size = System::Drawing::Size(170, 29);
			   this->textBox4->TabIndex = 17;
			   this->textBox4->Text = L"5";
			   // 
			   // button5
			   // 
			   this->button5->BackColor = System::Drawing::Color::Turquoise;
			   this->button5->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			   this->button5->Font = (gcnew System::Drawing::Font(L"新細明體", 12, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				   static_cast<System::Byte>(136)));
			   this->button5->ForeColor = System::Drawing::SystemColors::Control;
			   this->button5->Location = System::Drawing::Point(900, 109);
			   this->button5->Name = L"button5";
			   this->button5->Size = System::Drawing::Size(233, 54);
			   this->button5->TabIndex = 18;
			   this->button5->Text = L"quick sort";
			   this->button5->UseVisualStyleBackColor = false;
			   this->button5->Click += gcnew System::EventHandler(this, &Form1::button5_Click);
			   // 
			   // richTextBox5
			   // 
			   this->richTextBox5->Location = System::Drawing::Point(900, 199);
			   this->richTextBox5->Name = L"richTextBox5";
			   this->richTextBox5->Size = System::Drawing::Size(233, 140);
			   this->richTextBox5->TabIndex = 19;
			   this->richTextBox5->Text = L"";
			   // 
			   // textBox5
			   // 
			   this->textBox5->Location = System::Drawing::Point(666, 13);
			   this->textBox5->Name = L"textBox5";
			   this->textBox5->Size = System::Drawing::Size(170, 29);
			   this->textBox5->TabIndex = 21;
			   this->textBox5->Text = L"100";
			   this->textBox5->TextChanged += gcnew System::EventHandler(this, &Form1::textBox5_TextChanged);
			   // 
			   // label5
			   // 
			   this->label5->AutoSize = true;
			   this->label5->Location = System::Drawing::Point(592, 16);
			   this->label5->Name = L"label5";
			   this->label5->Size = System::Drawing::Size(58, 18);
			   this->label5->TabIndex = 20;
			   this->label5->Text = L"steps =";
			   this->label5->Click += gcnew System::EventHandler(this, &Form1::label5_Click);
			   // 
			   // richTextBox1
			   // 
			   this->richTextBox1->Location = System::Drawing::Point(84, 199);
			   this->richTextBox1->Name = L"richTextBox1";
			   this->richTextBox1->Size = System::Drawing::Size(233, 140);
			   this->richTextBox1->TabIndex = 2;
			   this->richTextBox1->Text = L"";
			   // 
			   // Form1
			   // 
			   this->AutoScaleDimensions = System::Drawing::SizeF(9, 18);
			   this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			   this->ClientSize = System::Drawing::Size(1501, 388);
			   this->Controls->Add(this->textBox5);
			   this->Controls->Add(this->label5);
			   this->Controls->Add(this->richTextBox5);
			   this->Controls->Add(this->button5);
			   this->Controls->Add(this->textBox4);
			   this->Controls->Add(this->label4);
			   this->Controls->Add(this->label3);
			   this->Controls->Add(this->textBox3);
			   this->Controls->Add(this->checkBox2);
			   this->Controls->Add(this->checkBox1);
			   this->Controls->Add(this->richTextBox4);
			   this->Controls->Add(this->richTextBox3);
			   this->Controls->Add(this->button4);
			   this->Controls->Add(this->button3);
			   this->Controls->Add(this->richTextBox2);
			   this->Controls->Add(this->button2);
			   this->Controls->Add(this->textBox2);
			   this->Controls->Add(this->label2);
			   this->Controls->Add(this->label1);
			   this->Controls->Add(this->richTextBox1);
			   this->Controls->Add(this->textBox1);
			   this->Controls->Add(this->button1);
			   this->ForeColor = System::Drawing::SystemColors::ControlText;
			   this->FormBorderStyle = System::Windows::Forms::FormBorderStyle::Fixed3D;
			   this->Name = L"Form1";
			   this->Text = L"Form1";
			   this->ResumeLayout(false);
			   this->PerformLayout();

		   }
#pragma endregion

	private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e) {
		int n = Int32::Parse(textBox1->Text); // 讀取 n
		int range = Int32::Parse(textBox2->Text); // 讀取 rangeox2->Text); // 讀取 range
		Random^ data = gcnew Random(); // 建立亂數產生器
		richTextBox1->Clear(); // 清空之前的數據
		for (int i = 0; i < n; i++) {
			richTextBox1->AppendText("data{" + i.ToString() + "] = " + data->Next(range).ToString() + "\n"); // 產生亂數//輸出的字串後要加ToString()
		}
	}

		   void SelectionSort(array<int>^ data, int n) {
			   int i, j, min, temp;
			   for (i = 0; i < n - 1; i++)
			   {
				   min = i;
				   for (j = i + 1; j < n; j++) {
					   if (data[j] < data[min]) {
						   min = j;
					   }
				   }
				   if (min != i) {
					   temp = data[i];
					   data[i] = data[min];
					   data[min] = temp;
				   }
			   }
		   }
		   void Bubblesort(array<int>^ data, int n) {
			   int temp;
			   for (int i = n - 1; i > 0; i--) {
				   for (int j = 1; j <= i; j++) {
					   if (data[j - 1] > data[j]) {
						   temp = data[j];
						   data[j] = data[j - 1];
						   data[j - 1] = temp;
					   }
				   }
			   }

		   }
		   void QuickSort(array<int>^ data, int left, int right) {
			   if (left < right) {
				   int pivot = data[right]; // 以最後一個元素作為樞軸
				   int i = left - 1;

				   for (int j = left; j < right; j++) {
					   if (data[j] <= pivot) {
						   i++;
						   // 交換 data[i] 和 data[j]
						   int temp = data[i];
						   data[i] = data[j];
						   data[j] = temp;
					   }
				   }
				   // 交換 data[i+1] 和 data[right] (將 pivot 放到正確位置)
				   int temp = data[i + 1];
				   data[i + 1] = data[right];
				   data[right] = temp;

				   int partitionIndex = i + 1;

				   // 遞迴處理左右兩部分
				   QuickSort(data, left, partitionIndex - 1);
				   QuickSort(data, partitionIndex + 1, right);
			   }
		   }


		   int Binarysearch(array<int>^ data, int n, int target) {
			   int left = 0;
			   int right = n - 1;

			   while (left <= right) {
				   int mid = left + (right - left) / 2;

				   if (data[mid] == target) {
					   return mid; // 找到目標值，返回索引
				   }
				   else if (data[mid] < target) {
					   left = mid + 1; // 目標值在右半部分
				   }
				   else {
					   right = mid - 1; // 目標值在左半部分
				   }
			   }

			   return -1; // 沒有找到目標值
		   }



	private: System::Void button2_Click(System::Object^ sender, System::EventArgs^ e)
	{
		int n = Int32::Parse(textBox1->Text); // 讀取 n)
		int repetitions = Int32::Parse(textBox4->Text);
		float total = 0;
		richTextBox2->Clear();
		for (int r = 0; r < repetitions; r++) {

			array<int>^ data = gcnew array<int>(n); // 建立一個陣列

			array<String^>^ lines = richTextBox1->Lines; //把舊資料按行提出


			for (int i = 0; i < n; i++) {//提data
				int position = lines[i]->IndexOf("=") + 2;//新數列提的資料位置要特別注意
				data[i] = Int32::Parse(lines[i]->Substring(position));//substring=擷取
			}


			//clock_t start = clock(); // 開始計時
			auto start = std::chrono::high_resolution_clock::now();

			// 開始排序
			SelectionSort(data, n); // 排序


			auto end = std::chrono::high_resolution_clock::now();
			//clock_t end = clock(); // 結束計時
			//float Time = float(end - start) / CLOCKS_PER_SEC; //  計算運行時間
			std::chrono::duration<double> Time = end - start;

			//richTextBox2->Clear();


			if (checkBox1->Checked) //  Echo Print 功能
			{
				for (int i = 0; i < n; i++)
				{
					richTextBox2->AppendText("data[" + i.ToString() + "] = " + data[i].ToString() + "\n");
				}
			}

			if (checkBox2->Checked) //  Self Check 功能
			{
				bool sorted = true;

				for (int i = 1; i < n; i++)
				{
					if (data[i - 1] > data[i])
					{
						sorted = false;
						break;
					}
				}
				richTextBox2->AppendText(sorted ? "Self Check for Sorted: Success!\n" : "Self Check for Sorted: Failed!\n");


			}
			richTextBox2->AppendText("CPU Time: " + Time.count().ToString("F6") + " sec\n");
			total += Time.count();
		}
		richTextBox2->AppendText("total CPU Time: " + total.ToString("F6") + " sec\n");

	}

	private: System::Void button3_Click(System::Object^ sender, System::EventArgs^ e) {
		int n = Int32::Parse(textBox1->Text); // 讀取 n)
		int repetitions = Int32::Parse(textBox4->Text);
		float total = 0;
		richTextBox3->Clear();
		for (int r = 0; r < repetitions; r++) {

			array<int>^ data = gcnew array<int>(n); // 建立一個陣列
			array<String^>^ lines = richTextBox1->Lines; //把舊資料按行提出


			for (int i = 0; i < n; i++) {//提data
				int position = lines[i]->IndexOf("=") + 2;//新數列提的資料位置要特別注意
				data[i] = Int32::Parse(lines[i]->Substring(position));//substring=擷取
			}

			auto start = std::chrono::high_resolution_clock::now();
			//clock_t start = clock(); // 開始計時


			// 開始排序
			Bubblesort(data, n); // 排序


			auto end = std::chrono::high_resolution_clock::now();
			//clock_t end = clock(); // 結束計時
			//float Time = float(end - start) / CLOCKS_PER_SEC; //  計算運行時間
			std::chrono::duration<double> Time = end - start;

			//richTextBox3->Clear();


			if (checkBox1->Checked) //  Echo Print 功能
			{
				for (int i = 0; i < n; i++)
				{
					richTextBox3->AppendText("data[" + i.ToString() + "] = " + data[i].ToString() + "\n");
				}
			}

			if (checkBox2->Checked) //  Self Check 功能
			{
				bool sorted = true;

				for (int i = 1; i < n; i++)
				{
					if (data[i - 1] > data[i])
					{
						sorted = false;
						break;
					}
				}
				richTextBox3->AppendText(sorted ? "Self Check for Sorted: Success!\n" : "Self Check for Sorted: Failed!\n");


			}
			richTextBox3->AppendText("CPU Time: " + Time.count().ToString("F6") + " sec\n");
			//Time.ToString("F6")
			total += Time.count();
		}
		richTextBox3->AppendText("total CPU Time: " + total.ToString("F6") + " sec\n");
	}


	private: System::Void button5_Click(System::Object^ sender, System::EventArgs^ e) {
		int n = Int32::Parse(textBox1->Text); // 讀取 n)
		int repetitions = Int32::Parse(textBox4->Text);
		float total = 0;
		richTextBox5->Clear();
		for (int r = 0; r < repetitions; r++) {
			array<int>^ data = gcnew array<int>(n); // 建立一個陣列

			array<String^>^ lines = richTextBox1->Lines; //把舊資料按行提出


			for (int i = 0; i < n; i++) {//提data
				int position = lines[i]->IndexOf("=") + 2;//新數列提的資料位置要特別注意
				data[i] = Int32::Parse(lines[i]->Substring(position));//substring=擷取
			}

			auto start = std::chrono::high_resolution_clock::now();
			//clock_t start = clock(); // 開始計時


			// 開始排序

			QuickSort(data, 0, n - 1);
			// 排序


			auto end = std::chrono::high_resolution_clock::now();
			//clock_t end = clock(); // 結束計時
			//float Time = float(end - start) / CLOCKS_PER_SEC; //  計算運行時間
			std::chrono::duration<double> Time = end - start;

			//richTextBox5->Clear();


			if (checkBox1->Checked) //  Echo Print 功能
			{
				for (int i = 0; i < n; i++)
				{
					richTextBox5->AppendText("data[" + i.ToString() + "] = " + data[i].ToString() + "\n");
				}
			}

			if (checkBox2->Checked) //  Self Check 功能
			{
				bool sorted = true;

				for (int i = 1; i < n; i++)
				{
					if (data[i - 1] > data[i])
					{
						sorted = false;
						break;
					}
				}
				richTextBox5->AppendText(sorted ? "Self Check for Sorted: Success!\n" : "Self Check for Sorted: Failed!\n");


			}
			richTextBox5->AppendText("CPU Time: " + Time.count().ToString("F6") + " sec\n");
			//Time.ToString("F6")
			total += Time.count();
		}
		richTextBox5->AppendText("total CPU Time: " + total.ToString("F6") + " sec\n");
	}

	private: System::Void button4_Click(System::Object^ sender, System::EventArgs^ e) {
		int n = Int32::Parse(textBox1->Text); // 讀取 n)
		float total = 0;
		int target = Int32::Parse(textBox3->Text);
		int repetitions = Int32::Parse(textBox4->Text);
		richTextBox4->Clear();
		for (int r = 0; r < repetitions; r++) {

			array<int>^ data = gcnew array<int>(n); // 建立一個陣列

			array<String^>^ lines = richTextBox1->Lines; //把舊資料按行提出


			for (int i = 0; i < n; i++) {//提data
				int position = lines[i]->IndexOf("=") + 2;//新數列提的資料位置要特別注意
				data[i] = Int32::Parse(lines[i]->Substring(position));//substring=擷取
			}

			auto start = std::chrono::high_resolution_clock::now();
			//clock_t start = clock(); // 開始計時


			QuickSort(data, 0, n - 1);
			int result = Binarysearch(data, n, target);


			auto end = std::chrono::high_resolution_clock::now();
			//clock_t end = clock(); // 結束計時
			//float Time = float(end - start) / CLOCKS_PER_SEC; //  計算運行時間
			std::chrono::duration<double> Time = end - start;

			//richTextBox4->Clear();


			if (result != -1) {
				richTextBox4->AppendText("Target found at index: " + result.ToString() + "\n");
			}
			else {
				richTextBox4->AppendText("Target not found.\n");
			}

			if (checkBox1->Checked) //  Echo Print 功能
			{
				for (int i = 0; i < n; i++)
				{
					richTextBox4->AppendText("data[" + i.ToString() + "] = " + data[i].ToString() + "\n");
				}
			}
			/*
			if (checkBox2->Checked) //  Self Check 功能
			{
				bool sorted = true;

				for (int i = 1; i < n; i++)
				{
					if (data[i - 1] > data[i])
					{
						sorted = false;
						break;
					}
				}
				richTextBox4->AppendText(sorted ? "Self Check for Sorted: Success!\n" : "Self Check for Sorted: Failed!\n");


			}
			*/
			richTextBox4->AppendText("CPU Time: " + Time.count().ToString("F6") + " sec\n");
			//Time.ToString("F6")
			total += Time.count();
		}
		richTextBox4->AppendText("total CPU Time: " + total.ToString("F6") + " sec\n");
	}

	private: System::Void label5_Click(System::Object^ sender, System::EventArgs^ e) {
	}
private: System::Void textBox5_TextChanged(System::Object^ sender, System::EventArgs^ e) {
	}
private: System::Void chart1_Click(System::Object^ sender, System::EventArgs^ e) {
}
};

};





</pre>