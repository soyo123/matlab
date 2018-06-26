# matlab
function min =  steepestDescent(x0,eps,sp1,h)
%最急降下法
%
%xk
global k
k=0;
xk=x0;
%勾配dxを求める
dx=dfun(xk,eps);
%探索方向sk
sk=-dx;%%%%%%%%%%%%%%%%%%%%%
%dxの模
ldx=sqrt(sum(dx.^2));%%%%%%%%%%%%%%%%%%%%%%%%%
%循環（終了条件）
while ldx>eps
    alpha=lineSearch(sp1,h,eps,xk,dx);
   % fprintf('alpha=%f\n',alpha);
    %新xk
    
    xk=xk+alpha*sk;
    k=k+1;
  %  disp(xk);
%     fprintf('xk=%f\n',xk);
    %勾配dxを求める
    dx=dfun(xk,eps);
    %探索方向sk
    sk=-dx;
    %dxの模
    ldx=sqrt(sum(dx.^2));%%%%%%%%%%%%%%%%%%%%%%%
 end
min=xk;
end

