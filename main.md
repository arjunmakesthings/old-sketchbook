***
### kucch crazy ho gaya #punctual 

``` c
--bg


o << 0.2; 

r << 0.1; 
g << 0.02; 
b << 0.08;  

-- top square 
spin[osc(cam*0.002)] $ 
rect [cam,0] [2,2] * o * [r,cam/2,cam/0.8]* o>> video;

[0,0,0] >> video; 
```

![[Screenshot 2024-03-20 at 10.53.51 PM.png]]
![[Screenshot 2024-03-20 at 10.55.02 PM.png]]

22:55, 2024-03-20
***
### face in rectangle #punctual 
Trying to clip face to make typography. I don't understand what's happening, but let's see. I'll figure it out. 

``` c
[0,0,0] >> video; 

o << 1; 

rect [0, 0] $ 
[cam] * o >> video; 
```

![[Screenshot 2024-03-20 at 10.32.19 PM.png]]

22:32, 2024-03-20
***
### in progress #punctual 

``` c
o << 0.8;

x << [-2, -1.9 .. 2]; 
y << 0; 

w << 0.2; 

-- [1,1,1] >> video; 

[0,0,0] >> video; 

r << 0.2; 
g << 0.8; 
b << 0.1; 

w << 0.02; 

spin [osc(pi*0.02)] $ fit (1/1) $ rect [x, y] [w,w] * o >> video; 
```

***
### repeating video input in the shape of a flower #punctual 
Repeat video input in the shape of a flower. 

``` c
-- video flower

z << 0.8; 

a << [0, 0.2 .. 1]; 

o << 0.3; 


r << 1; 
g << 0.31; 
b << 0.61; 

col << [r,g,b]*o;

z2 << 0.9;  

zoom [z2*(-1), z2] $ tile [2, 2] [[fit (1/1) $ spin [a] $ [zoom[(z*(-1)),z] [cam]]]]* o * [col]>> video; 
```

![[Screenshot 2024-03-17 at 10.21.41 PM.png]]

22:20, 2024-03-17
***
### making an 'a' with video input #punctual 
Made a lower-case 'a' with shaders on Punctual. 

``` c 
-- creating an A

s << 0.1; 

x << [0, 0.1 .. 0.5]; 
y << [0]; 

o << 0.4; 

r << 0.1; 
g << [x]*0.08; 
b << 0.8; 


z << 0.18; 

spinVal << 0; 

-- bar 

spin [osc(spinVal)] [move [x,0.7] [zoom [(z*(-1)), z] (fit (0.02/0.02) $ cam) * o  *[r,g,b]]] >> video; 

-- center

midStem << [-0, -0.1 .. 0.85]; 

spin [ osc(spinVal)] [move [0.5,midStem] [zoom [(z*(-1)), 0.5] (fit (0.02/0.02) $ cam) * o *[r,g,b]]] >> video; 

-- bottom 

spin [ osc(spinVal)] [move [x,-0.5] [zoom [(z*(-1)), z] (fit (0.02/0.02) $ cam) * o *[r,g,b]]] >> video; 

spin [osc(spinVal)] [move [x,midStem+0.2] [zoom [(z*(-1)), 0.05] (fit (0.02/0.02) $ cam)* o *[r,g,b]]] >> video; 

spin [osc(spinVal)] [move [-0.0005,midStem-0.29] [zoom [(z*(-1)), 0.5] (fit (0.02/0.02) $ cam) * o  *[r,g,b]]] >> video; 
```

![[Screenshot 2024-03-16 at 9.00.53 PM.png]]

21:02, 2024-03-16
***
### make rows of video feed

``` c
z << 0.1; 
x << [0, 0.1 .. 0.5]; 

move [x,0] [zoom [(z*(-1)), z] (fit (0.02/0.02) $ cam)] >> video; 
```

***
### noisy background #punctual 
Grey, noisy background. 

``` c
0, 0, 0 >> video;

x << osc ([fx*0.2]*0.08);
y << osc ([fy*0.0002]*0.2);  

w << osc(fr*0.5)*0.7;
h << 1;

-- r << 0.5; 
-- g << 0.5; 
-- b << 0.5; 

rect [x, y] [w, h] *0.3 >> video;

---

0, 0, 0 >> video;

-----------------------
r << [0.1, osc (fx)*0.7, fr*0.2]; 
g << 0; 
b << [1, 0, 0.3]; 

x1 << osc [((fr*fy)), fr], fr; 
y1 << 0; 

w << [0.1, 0.2, 0.2]; 
h << [fy, fx, 2]; 

rect [x1,y1] [w, h] * [0.8] * [r,g,b] >> video; 
```

***
### ripple #punctual 
Makes a water ripple. 

``` c 
0, 0, 0 >> video; 

w << fr/0.02; 

h << 2; 

v << (ft*0.02); 

spin [osc(fr*0.002)*sin(fx*0.0002)*cos(fx)] (move [osc(fx*0.000008), ft*4] (hline [v*0.002] [w*10, h] * 0.8 * [osc(fx*0.002),0.1*v, osc(v*0.3)])) >> video;
```

***
### water #punctual {{date}}
Simulates something of a water kind. 

```c
x << [0.3,0.2,0.3,0.8]; 

move[sin(fx+fy*(1/4*fr)*fr), 0] [circle [x, fy][1.4]*0.8 * [0.1, 0.2, 0.3]] >> video; 
```
  ***


