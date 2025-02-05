# Cursor Animations
I have personally never done to much with code in general and everyone in their life has to make a mouse trail so my thought was that would be a good next step. I tried to pull inspiration from old windows 7 screensavers i saw while i was in highshool and add my own flair and twist to them within the bounds of my capabilities so I hope you enjoy the 4 I came up with. 

- The big things i did we learn how to use millis to track time and use that as a stop watch almost to change colors, along side a few other skill in class to if/else my way through the full cursor shift and the changing what the background color is getting a changed to.


```
var time;
var wait = 2000; // change this to change the 'ticking'
var c;
var trail = [];

function setup() {
  createCanvas(400, 400);
  noStroke();
  time = millis();
  c = 255;
  v = color(0);
}

function draw() {
  
  // store mouse position to an array
  trail.push([mouseX, mouseY]);
  //console.log(trail); // print to see stored mouse positions
 
  fill(v);
  //if loops that change the cursor shape and color after a set amount of time
  if( frameCount < 1000 ) {
    background(c);
    c = c - 0.25
  
    
  // draw ellipses at stored mouse positions
      for (i=0; i<trail.length; i++) {
         let s = 70*(i/trail.length);// size
      ellipse(trail[i][0], trail[i][1], s);
    }
  }
  
    else if( frameCount < 2000 ) {
      
      c = c + 0.25
     background(c,0,0)
    
      for (i=0; i<trail.length; i++) {
       let s = 140*(i/trail.length);
      ellipse(trail[i][0], trail[i][1], s,10);
    }
  }
  
      else if( frameCount < 3000 ) {
     c = c - 0.25
     background(c,0,0)
 
  
      for (i=0; i<trail.length; i++) {
       let s = 240*(i/trail.length);
      ellipse(trail[i][0], trail[i][1], 10,s);
    }
  }
  else if( frameCount < 6000 ) {
     c = c + 0.25
     background(0,0,c)
 
  
      for (i=0; i<trail.length; i++) {
       let s = 180*(i/trail.length);
      ellipse(trail[i][0], trail[i][1], s , 30);
    }
  }
  
  
    if ((millis() - time) >= wait) {
    v = color(random(255), random(255), random(255))
    time = millis(); //also update the stored time
    }
  // when the length of the list is greater than 50, remove 
  // the first element in the list (oldest..end of trail)
  if (trail.length > 50) {
    trail.shift();
  }

}
```

https://editor.p5js.org/Amaterasu903/sketches/EgUj-jQMO
Feel free to play around Its a bit scuffed but Im learning and its pretty cool what im starting to grasp
