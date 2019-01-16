---
layout: project
type: project
image: images/micromouse.jpg
title: Air Hocky
permalink: projects/micromouse
# All dates must be YYYY-MM-DD format!
date: 2017-12-10
labels:
  - College Project
  - Java
summary: My team developed a simple air hocky game on Eclipes.
---
img class="ui image" src="airhocky.PNG">

My first major project as an ICS student was creating an air hocky game using Java. Five month prior to creating this project I only learned how to print Hello World with Java. Fortunately with the help of some outside libraries and my awesome professors and TAs, I was able to complete a project such as this one. Hopefully this game will be a good guideline to see my development and growth as a programmer. 



Here is the code for the main function:

```js
public static void main(String[] args) throws java.io.IOException
	{
		//Opening the map
		File table = new File("table");
									
		//scanning the map
		Scanner scan = new Scanner(table);
							
		//reading first 2 numbers to determine the size of canvas
		int width = scan.nextInt();
		int height = scan.nextInt();
						
		//Initializing screen
		EZ.initialize(width * 32 - 5, height *32 -25);
		EZ.setBackgroundColor(new Color(23, 137, 24));
		
		EZ.addImage("table.png", 480, 305);
		
		//Run function setUp in object map
		Map map = new Map();
		map.setUp();
		
		
		//initialize the clock text
		clock = EZ.addText(492, 100, "", Color.BLACK, 50);
		
		//score for player1
		EZ.addText("BAUHS93.TTF", 200, 100, "Player 1: ", Color.RED, 50);
		score1 = EZ.addText("BAUHS93.TTF", 320, 100, "", Color.RED, 50);
		//score for player2
		EZ.addText("BAUHS93.TTF", 760, 100, "Player 2: ", Color.BLUE, 50);
		score2 = EZ.addText("BAUHS93.TTF", 870, 100, "", Color.BLUE, 50);
		
		//load pucks
		Puck puck = new Puck("Puck.png", 500, 300, 5, 5);
		
		//load player pucks					
		Striker player1 = new Striker("Striker.png",250,300, 'w', 's', 'a', 'd', 'b');
		StrikerTwo player2 = new StrikerTwo("Striker2.png",750,300,'i','k', 'j', 'l');
		
		//background music
		bgm.play();
		
		while(gameState == 0)
		{
			timer();
			player1.controlStriker();
			player2.controlStriker();
			puck.puckBehavior();
			
			 
			if (player1.strikerX()>455)
			{
				Striker.posx=Striker.posx-5;
			}
			if (player2.strikerX()<535)
			{
				StrikerTwo.posx=StrikerTwo.posx+5;
			}
			EZ.refreshScreen();
			
		} //while(true)
		
		//end game text
		if(Puck.point1 > Puck.point2)
		{
			EZ.addText("BAUHS93.TTF", 492, 300, "Player 1 Wins! ", Color.RED, 50);
			bgm.stop();
			victory.play();
		}
		else
		{
			EZ.addText("BAUHS93.TTF", 492, 300, "Player 2 Wins! ", Color.BLUE, 50);
			bgm.stop();
			victory.play();
		}
	
	} //main

```




