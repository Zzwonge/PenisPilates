//# PenisPilates
//Studentwork

//PImage bg;
//Menu_Start menu_start;
//Menu_Ego menu_ego;
//Menu_Pilates menu_pilates;
//Menu menu;
Pilates pilates;
Ego ego;
Anim_Sound anim_sound;


void setup() {

  size(800, 640);

  //menu = new Menu();
  anim_sound = new Anim_Sound();
  pilates = new Pilates("bitchAni.png", 12, "jjkklllkkj");
  ego = new Ego("spritzAni.png", 7, "yyxxcccxxy");
}

void draw() {
  //menu_start.draw(); 
  //menu_ego.draw();
  //menu_pilates.draw();
  //menu.draw();
  anim_sound.draw();
  // was ist der aktuelle stand der spieler?
  // is einer fertig, ist das spiel vorbei
  if (ego.isDone()) {
    println("DONE!");
    exit();
  }
  
  // der spieler stellt seinen status dar.
  ego.draw();
  pilates.draw();
}

void keyPressed() {
  // welche taste wurde gedrückt?
  
  // gehört die taste zu einem spieler?
  if (ego.reactsToKey(key)) {
    // wenn ja -> spieler -> mach deine aktion
    ego.update(key);
  }

  if (pilates.reactsToKey(key)) {
    boolean updatedPilates = pilates.update(key);

    if (updatedPilates) {
      ego.inc();
    }
  }
}
//fullscreen 
boolean sketchFullScreen()
{
  return false;
}
