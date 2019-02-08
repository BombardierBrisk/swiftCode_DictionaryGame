# swiftCode_DictionaryGame
First assignment for IOS Development
//
//  main.swift
//  AljonRamos_A1_DictionaryGame
//
//  Created by Tech on 2019-02-08.
//  Copyright © 2019 Tech. All rights reserved.
//

import Foundation

var game_Start:Bool = false;
var game_Continue:Bool = false;
var game_Score = 0;

func game_Dictionary() -> [String:String]{
    let dictionary = [  "string":"string", //key; definition
                        "Hello": "Greeting to other person",
                        "Bye": "A fare well to a person",
        "charge":"A large force heads directly to an enemy to engage in close quarters combat, with the hope of breaking the enemy line.",
        "ambush":" Carrying out a surprise attack on an enemy that passes a concealed position.",
        "overwatch":"When one small unit provides support for another.",
        "siege":" A military blockade of a city or fortress with the intent of conquering by force or attrition.",
        "tank":"Is an armoured fighting vehicle designed for front-line combat, with heavy firepower, strong armour.",
        "pillbox":"A small concrete guard post.",
        "infiltrate":"The passing of troops in small groups through an entrance in the enemy's side; silently",
        "rebellion":" Refers to open resistance that is organized and armed against the government.",
        "mother of all bombs":"A nickame the Air Force gave to its 22,000-pound MOAB",
        "brigade":"Consists of three or more battalions totaling 2,500 to 5,000 soldiers, commanded by a colonel.",
        "squad":"Four to 10 soldiers commanded by a staff sergeant.",
        "casualties ":"comprise of both dead and wounded.",
        "reload":"The manual procedure of inserting a magazine, clip, belt, or single round into a weapon",
        "grenade":"Explosive throwable item",
        "zero":"Japanese plane that was nicknamed by a number.",
        "patton":"Follow me, follow me, or get out of my way. General George ________",
        "churchill":"We will fight on the beaches, will fight in the air; we will never surrender. Winston ______",
        "blitzkrieg":"A German term for lightning war. Punched through Poland's defenses within no time.",
        "tiger":"A nickname for a WWII German heavy tank",
        "panther":"A nickname for a WWII German medium tank",
        "x-wing":"this fighter killed the Death Star in Star Wars _-____",
        "dday":"We will accept nothing less than full victory! Good luck! And let us all beseech the blessing of Almighty God upon this great and noble undertaking.",
        "panzer":"Armour became a general term for German tanks.",
        "omaha":"Beach code-named for the US army landing on june 6th 1944.",
        "yankee":"British nickname for American troops.",
        "jerry":"Allied nickname for German troops.",
        "retreat":"Not sufficient resources on the front line; requires all troops to leave area.",
        "coward":"Not able to do your duty on the frontlines in battle even when not injured.",
        "chile":"A republic in southern South America on the western slopes of the Andes on the south Pacific coast.",
        "humiliating":"Causing embarrassment or awareness of your shortcomings.",
        "saddam":"Iraqi leader who waged war against Iran. (first name)",
        "civilian":"A nonmilitary citizen.",
        "fascist":"An adherent of right-wing authoritarian views.",
        "eradicate":"Destroy completely, as if down to the roots.",
        "famine":"A severe shortage of food resulting in starvation and death.",
        "commission":"A special group delegated to consider some matter.",
        "knight":"A person of noble birth trained to arms and chivalry.",
        "skill":"An ability that has been acquired by training.",
        "territory":"The geographical area under the jurisdiction of a state.",
        "flag":"A rectangular piece of cloth of distinctive design.",
        "level":"A relative position or degree of value in a graded group.",
        "range":"A variety of different things or activities.",
        "crew":"The men or women who man a vehicle.",
        "attribute":"A quality belonging to or characteristic of an entity.",
        "oppress":"Come down on or keep down by unjust use of one's authority.",
        "jet":"An airplane powered by gas turbines."
    ]
    return dictionary;
}

func UserInput(){
    if !game_Start{
        print("Press Yes or No to play (y/n). !!!!!!No Capital Letters!!!!!!");
    }
    else {
        print("Do you want to play Again? (y/n). !!!!!!No Capital Letters!!!!!!");
    }
    
    let answer = readLine();
    
    if answer?.caseInsensitiveCompare("y") == .orderedSame {
        game_Start = true;
        game_Continue = true;
        print("Lets Play! Remember no CAPS ALLOWED!");
    } else {
        print ("Leaving Game");
        if(game_Start){
            print("Total Score: \(game_Score)");
        }
        game_Continue = false;
        
        
    }
}

func PlayGame(){
    let game_Dic:[String:String] = game_Dictionary();
    UserInput()
    
    while game_Continue {
        let random_Num = Int(arc4random_uniform(UInt32(game_Dic.count))); //Gets random number to dictionary.
        let term = Array(game_Dic)[random_Num].key;
        let explanation = Array(game_Dic)[random_Num].value;
        
        print(explanation);
        let answer = readLine();
        
        if answer == term{
            print("Correct");
            game_Score += 1;
        }
        else{
            print("You are wrong. You can try again.");
            let answer_Again = readLine();
            
            if answer_Again == term{
                print("Correct");
                game_Score += 1;
                }
            else {
                print("Wrong again. The answer is \(term)");
            }
        
            }
    }
    
    if game_Dic.count > 0 {
        UserInput()
    }
    else {
        print("Game Over. Your score: \(game_Score)")
    }
    
}

PlayGame();
