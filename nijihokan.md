# matlab
function outputArg = nijihokan(xAr,yAr,eps,x,dx)
%二次補完法
%

% fprintf('xAr=%f\n',xAr);
% fprintf('yAr=%f\n',yAr);

%初期値
if xAr(1)>xAr(3)%
    x1=xAr(3);
    x2=xAr(2);
    x3=xAr(1);
    y1=yAr(3);
    y2=yAr(2);
    y3=yAr(1);
else
    x1=xAr(1);%%%%%%%%%%%
    x2=xAr(2);
    x3=xAr(3);
    y1=yAr(1);
    y2=yAr(2);
    y3=yAr(3);
end
x0=1/2*((x2^2-x3^2)*y1+(x3^2-x1^2)*y2+(x1^2-x2^2)*y3)/((x2-x3)*y1+(x3-x1)*y2+(x1-x2)*y3);
y0=dun(x0,x,dx);
if x0==x2
    x0=x0+eps/3;%%%%%%%%%%%%%%%%
end

%     fprintf('x1=%f\n',x1);
%     fprintf('y1=%f\n',y1);
%     fprintf('x2=%f\n',x2);
%     fprintf('y2=%f\n',y2);
%     fprintf('x3=%f\n',x3);
%     fprintf('y3=%f\n',y3);
%     fprintf('x0=%f\n',x0);
%     fprintf('y0=%f\n',y0);

%循環（終了条件判断）
% while abs(x1-x3)>eps
%     %新区間
%     if x0<x2
%         if y0<y2
%             x3=x2;
%             y3=y2;
%             x2=x0;
%             y2=y0;
%         elseif y2<y0
%             x1=x0;
%             y1=y0;
%         else
%             if abs(x2-x1) <= abs(x3-x2)
%                 x3=x2;
%                 y3=y2;
%                 x2=x0;
%                 y2=y0;
%             else
%                 x1=x0;
%                 y1=y0;
%             end
%         end
%     else
%         if y2<y0
%             x1=x2;
%             y1=y2;
%             x2=x0;
%             y2=y0;
%         elseif y2>y0
%             x3=x0;
%             y3=y0;
%         else
%             if abs(x2-x1) <= abs(x3-x2)
%                 x3=x0;
%                 y3=y0;
%             else
%                 x1=x2;
%                 y1=y2;
%                 x2=x0;
%                 y2=y0;
%             end
%         end
%     end
%     %新x0
%     x0=1/2*((x2^2-x3^2)*y1+(x3^2-x1^2)*y2+(x1^2-x2^2)*y3)/((x2-x3)*y1+(x3-x1)*y2+(x1-x2)*y3);
%     y0=dun(x0,x,dx);
%     if x0==x2
%         x0=x0+eps;
%     end
% %      fprintf('x1=%0.20f x2=%0.20f x3=%0.20f x0=%0.20f delta=%0.20f\n',x1,x2,x3,x0,abs(x1-x3));
% %      fprintf('y1=%0.20f y2=%0.20f y3=%0.20f y0=%0.20f\n\n',y1,y2,y3,y0);
% end
% %出力x0




while abs(x1-x3)>eps
    
if x0<x2 && y0>y2
    x1=x0;
    x2=x2;
    x3=x3;
    y1=y0;
    y2=y2;
    y3=y3;
end
if x0<x2 && y0<y2
    x1=x1;
    x3=x2;
    x2=x0;
    y1=y1;
    y2=y0;
    y3=y2;
end
 if x0>x2 && y0>y2
    x1=x1;
    x2=x2;
    x3=x0;
    y1=y1;
    y2=y2;
    y3=y0;
 end   
 if x0>x2 && y0<y2
    x1=x2;
    x2=x0;
    x3=x3;
    y1=y2;
    y2=y0;
    y3=y3;
    
end   
x0=1/2*((x2^2-x3^2)*y1+(x3^2-x1^2)*y2+(x1^2-x2^2)*y3)/((x2-x3)*y1+(x3-x1)*y2+(x1-x2)*y3);


  if abs(x0-x2)<eps/30 %%%%%%%%%%%%%
       
      if  abs(x1-x2)>abs(x3-x2)%%%%%%%%%%%%%
          x0=x2-eps/20;%%%%%%%%%%%%%%%
      else 
          x0=x2+eps/20;%%%%%%%%%%%%%
      end
          
  end
  y0=dun(x0,x,dx);%%%%%%%%%%%%%%%%
end





























outputArg=x0;
    %fprintf('outputArg=%f\n\n\n\n',outputArg);
end

