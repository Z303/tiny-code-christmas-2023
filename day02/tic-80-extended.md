# Day 2 Extended
![A spiral overlayed with three metaball exposing a plasma underneath](./day02extended.gif)

Based on the [day 2](https://github.com/Z303/tiny-code-christmas-2023/blob/main/day02/tic-80-extra.md) extra dn [last years day 10](https://github.com/Z303/tiny-code-christmas-2022/blob/main/day10/tic-80.md)

```
m=math 

w=240 
h=136

t=0

function TIC()
	for i=0,w*h do
		x=i%w
		y=i//w
		
		c=0
		for b=1,3 do
			a=b*2.56*m.pi/3
			s=b*1412+time()/7700
			
			u=w/2+m.sin(a+3.12*s)*((w/2)-27)
			v=h/2+m.sin(a+2.54*s)*((h/2)-27)
			
			c=c+h*w/3/((x-u)*(x-u)+(y-v)*(y-v))
		end
		val = m.min(m.max(c,10),15)
		
		if (val==15) then
		 r=99
			u=r*m.sin(t/h+x/w)
   v=r*m.sin(t/r+y/w)
   pix(x,y,u+v)
  else 
	  if (val==10) then
			 u=x-w/2
				v=y-h/2
			 val=t/16+(m.atan2(v,u)+math.pi)*2.546
	   pix(x,y,val)
			else
			 pix(x,y,val)
			end
		end
	end
	
	t=t+0.25
end
```

