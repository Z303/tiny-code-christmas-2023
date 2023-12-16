# Day 5 Extended
![A rotating cube of red spheres over a green ground plane fading out to the distance with a gradient blue sky](./day05extended.gif)

```
s=math.sin

w=240
h=68

angle=0
t=0 

sr=0x40
sg=0x40
sb=0xd0

er=0xd0
eg=0xd0
eb=0xff

gsr={0xa7,0xa7,0xa7,0xa7}
gsg={0xf0,0xf0,0xf0,0xf0}
gsb={0xff,0xff,0xff,0xff}

ger={0xa7,0x37,0x25,0x29}
geg={0xf0,0xb7,0x71,0x36}
geb={0x70,0x64,0x79,0x6f}

function setColour(r,g,b,idx)
	red=0x3FC0+idx*3
	green=red+1
	blue=red+2
	poke(red,r)
	poke(green,g)
	poke(blue,b)
end

function BDR(i)
 if i <= h then
 	cr=sr+((er-sr)/h)*i
 	cg=sg+((eg-sg)/h)*i
 	cb=sb+((eb-sb)/h)*i
 	setColour(cr,cg,cb,10)
 else
  for j=1,4 do
			z=i-h+0.1
			p=99/z

 		k=z
   
   cr=gsr[j]+((ger[j]-gsr[j])/h)*k
 		cg=gsg[j]+((geg[j]-gsg[j])/h)*k
 		cb=gsb[j]+((geb[j]-gsb[j])/h)*k
 		
   setColour(cr,cg,cb,j+4)
  end 
 end
end

function TIC()
 pts = {}
 for x=-25,25,6 do
 	for y=-25,25,6 do
 		for z=-25,25,6 do
 			d=s(angle)
 			c=s(angle-11)

 			px= x*c - y*d
 			py= x*d + y*c

 			qy= py*d + z*c

				pts[#pts+1]=
	    {x= px*c - qy*d,
	     y= py*c - z*d,
	     z= px*d + qy*c + 400}
 		end
 	end	
 end

	cls(10)
	
	for i=0,w*h do
		x=i%w
		y=i//w
		z=y+0.1
		
		q=(x-w/2)/z
		p=99/z
		o=s(t-11)
		
		u=o*q-s(t)*p
		v=s(t)*q+o*p 
		
		c=(u+t*3)//1&v//1
		pix(x,y+h,5+(c&3))
	end 
	
	table.sort(pts,function (a, b) 
			return a.z>b.z end)
	
 for p=1,#pts do 				 		
		for i=0,2 do 
			circ(pts[p].x*600/pts[p].z+120-i,
		      pts[p].y*600/pts[p].z+68-i,
		      3-i,i)
		end 
 end	
	
	t=t+.02
 angle=angle+.01	
end
```
