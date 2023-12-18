# Day 7 Extended
![A white snowflake make from six diamonds on a light blue background spinning](./day07extended.gif)

```
m=math
s=m.sin

w=120
h=68
a=30
b=10

t=0

function setColour(r,g,b,idx)
	red=0x3FC0+idx*3
	green=red+1
	blue=red+2
	poke(red,r)
	poke(green,g)
	poke(blue,b)
end

er=0x41
eg=0xa6
eb=0xf6

sr=0xff
sg=0xff
sb=0xff

for i=0,15 do
 cr=er+((sr-er)/15)*i
 cg=eg+((sg-eg)/15)*i
 cb=eb+((sb-eb)/15)*i
	setColour(cr//1,cg//1,cb//1,i)
end

function TIC()
	for i=0,w*2 do
	 for j=0,h*2 do
		 p=pix(i,j)
   if (p>0) then
    p=p-1
   end
			pix(i,j,p)
		end
	end

 for j=0,6 do
 	x={w,w-b,w,w+b,w}
		y={h,h-a,h-a*2,h-a,h}
 
 	c=t+j*m.pi/3  
 
 	for i=1,5 do
  	u=x[i]-w
  	v=y[i]-h
  	x[i]=w+s(c-11)*u-s(c)*v
 		y[i]=h+s(c)*u+s(c-11)*v
  end
  
  tri(x[1],y[1],x[2],y[2],x[4],y[4],15)
  tri(x[2],y[2],x[3],y[3],x[4],y[4],15)
 end
	
	t=t+0.03
end
```
