# Day 3 Extended
![Randomly moving pink balls that grow in size and become brighter as they get closer to each other. They trailing purple after-images. Lines join the balls if they get close enough](./day03extended.gif)

```
m=math
r=m.random

w=240
h=136

x={}
y={}

u={}
v={}

c={}

n=100 

s=100

for i=1,n do 
	x[i]=r(w)
	y[i]=r(h)
	
	u[i]=(r(s)-s/2)/s 
	v[i]=(r(s)-s/2)/s 
	
	c[i]=0 
end 

function setColour(r,g,b,idx)
	red=0x3FC0+idx*3
	green=red+1
	blue=red+2
	poke(red,r)
	poke(green,g)
	poke(blue,b)
end

cls(0)

sr=0xa0
sg=0x37
sb=0x80

er=0x30
eg=0x3f
eb=0x57

for i=0,14 do
 cr=er+((sr-er)/14)*i
 cg=eg+((sg-eg)/14)*i
 cb=eb+((sb-eb)/14)*i
	setColour(cr//1,cg//1,cb//1,i)
end

setColour(0xd0,0x77,0xb0,14)
setColour(0xff,0xff,0xff,15)

function TIC()
	for a=0,w do
	 for b=0,h do
		 p=pix(a,b)
   if (p>0) then
    p=p-1
   end
			pix(a,b,p)
		end
	end
	
	for i=1,n do 
		for j=1,n do 
			a=x[j]-x[i]
			b=y[j]-y[i]
			if a*a+b*b < 256 then 
				c[i]=c[i]+1
				line(x[j],y[j],x[i],y[i],15)
			end
		end
	end	
	
	for i=1,n do 
		circ(x[i],y[i],c[i],14)
		
		x[i]=(x[i]+u[i])%w
		y[i]=(y[i]+v[i])%h 
		
		c[i]=0 
	end

end
```
