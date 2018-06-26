# matlab
function min = lineSearch(x1,h,eps,x,dx)
%直線探査法
%
%囲い込み
[xAr,yAr]=kakoikonmi(x1,h,eps,x,dx);
%disp([xAr,yAr]);
%二次補間法
min=nijihokan(xAr,yAr,eps,x,dx);
end
