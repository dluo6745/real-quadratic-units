# real-quadratic-units
// Coding using magama 

S := function(p, m); // This function checks whether a prime p is split in a quadratic field K = Q(root(m)).
  K := QuadraticField(m);
  D := Discriminant(K);
    if (D mod p ne 0 and LegendreSymbol(D, p) eq 1) then
      return true;
    else
      return false;
    end if;
    
end function;

C := function(p, m); // This function the number of roots that are squares modulo p.
c := 0
K := QuadraticField(m);
u := FundamentalUnit(K);
f := MinimalPolynomial(u, Rationals());
F := GF(p); //Finite field of order p;
S := [KroneckerSymbol(x[1]) :  x in Roots(f, F)];
  for i := 1 to #S do
    if (S[i] eq 1) then
      c := c+1;
    end if;
  end for;
return c;



