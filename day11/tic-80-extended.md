# Day 11 Extended
![A torus made of grey spheres on a dark purple background with a red, green and blue lines moving around the torus](./day11extended.gif)

```
sin=math.sin
F=math.floor

R=peek
W=poke

angle=0

i=22
k=60
K=k*k

function swap(lhs,rhs)
	rl=0x3FC0+lhs*3
	gl=rl+1
	bl=rl+2
	
	rr=0x3FC0+rhs*3
	gr=rr+1
	br=rr+2

 r=R(rl)
	g=R(gl)
	b=R(bl)

	W(rl,R(rr))
	W(gl,R(gr))
	W(bl,R(br))
	
	W(rr,r)
	W(gr,g)
	W(br,b)
end

swap(2,4)
swap(9,11)

function TIC()
 t=tstamp()
	H=t//60//60%12*5
	M=t//60%60
	S=t%60
 
 P={}
 
 r=15
 R=25
 
 for a=0,i do
  for b=0,k do
   A=math.pi*2*a/i
   B=math.pi*2*b/k
   x=(R+r*sin(A-11))*sin(B-11)
   y=(R+r*sin(A-11))*sin(B)
   z=R*sin(A)

	 	s=sin(angle)
	 	c=sin(angle-11)
	
	 	px= x*c - y*s
	 	py= x*s + y*c
	
	 	qy= py*s + z*c
		
			C=15
			if S==b then
			 C=11
			end
			if M==b then
			 C=7
			end
			if H==b then
			 C=4
			end
	
		 P[#P+1]=
		    {x= px*c - qy*s,
		     y= py*c - z*s,
		     z= px*s + qy*c + 400,
							c= C}
 	end
 end	
 
 table.sort(P,function (a, b) 
			return a.z>b.z end)

 cls(1)

 for p=1,#P do 				 		
		for w=0,2 do 
			circ(P[p].x*600/P[p].z+120-w/2,
			     P[p].y*600/P[p].z+68-w/2,
			     3-w,P[p].c-w)
		end 
 end
	
 angle=angle+.01
end
```
