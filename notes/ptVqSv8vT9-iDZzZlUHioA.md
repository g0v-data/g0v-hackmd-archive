
	function setup() {
		createCanvas(windowWidth, windowHeight);// 給我視窗大小的畫布 //
	//createCanvas(100, 100); //給我寬為100，高為100的桌布

		background(100);//顏色 
	//background(231,108,247);// rgb設定背景顏色為(231,108,247)
	//background("#9999CC");
}
	function draw() {
		fill(mouseX % 255 , mouseY% 255,0)//要寫在第一行
		//充滿顏色 %255=鼠標隨著滑鼠位置有不同的顏色
		//ellipse(mouseX, mouseY, 20, 20)
			//左上角為0.0 x是橫 y是豎
		//橢圓       大        //寬,高; 
			//rect(	mouseX,mouseY,40);	//畫框框 鼠標在框框左上角
		 	 fill(mouseX %256,mouseY%256,0)
			//rect(mouseX-20,mouseY-20,40); // 畫框框 鼠標在框框中間
	
		
		if(mouseIsPressed)// 當mouseIsPressed為真(true)代表將執行下面程式（按下）
			{
				fill(255,255,0); //設置黃色
				ellipse(mouseX, mouseY, 20,20); //畫橢圓 寬為20 高為20 
				//根據上面的代碼可得出當按下滑鼠就會變成黃色的橢圓
			}
		 	 else //如果條件為false就會執行下面的程式
			{ //(沒有按下滑鼠
				rect(mouseX-20,mouseY-20,40);// 畫框框 鼠標在框框中間
			}
		
		
}	
		