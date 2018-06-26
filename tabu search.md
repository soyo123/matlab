# matlab
 clear all
 clc
kmax=100;
TL = 15;
select=2;
T = zeros(TL,1);
 HYOKA = 0;
    switch select
        case 1
            load initial_solution_20bit;
            [element,weight_limit,bit,initial_solution]=BenchmarkProblem(1);

        case 2
            load initial_solution_50bit;
            [element,weight_limit,bit,initial_solution]=BenchmarkProblem(2);

        case 3
            load initial_solution_100bit;
           [element,weight_limit,bit,initial_solution]=BenchmarkProblem(3);

        case 4
            load initial_solution_500bit;
           [element,weight_limit,bit,initial_solution]=BenchmarkProblem(4);

        case 5
            load initial_solution_1000bit;
            [element,weight_limit,bit,initial_solution]=BenchmarkProblem(5);
    end
for m=1: 50
x = initial_solution(m,1:bit); 
X= zeros(bit,bit);%近傍N(S）
gbest2= 0;
gbest = 0;
k=1;
 %近傍N（S）をつくる 
 for I = 1:kmax
        for i = 1:bit
            X(i,:) = x;
            X(i,i) = not(x(i));
        end
        
    %タブーリストに含まれる解を削除 
        for i = 1:bit
            for t = 1:TL
                if T(t,1)==0
                elseif X(i,T(t,1)) == not(x(1,T(t,1)) ) && T(t,1)~=0
                    X(i,:) = zeros(1,bit);
                    break
                else
                end
            end
            ANY(i,1) = any(X(i,:));
        end

        ii = 1;
        for i = 1:bit
            if ANY(i,1) == 0
               X(ii,:) = [];
            else
                ii = ii+1;
            end
        end
      
        %Step 3：評価値
            Y = X * element';
            L = length(Y(:,1));
            HYOKA = HYOKA + L;
        %ペナルティ
        for i=1:L
            if Y(i,2) > weight_limit
                Y(i,1) = 0;
            end
        end
        
        %gbest = gbest_new;
        [gbest2, N]  = max(Y(:,1));
        [A, B] = min(Y(:,2));
        
        %Step 4:終了条件（解の移動）
        if gbest2 == 0
            xa = x;
            x2 = x;
            x = X(B,:);
            Suii(k,1) = gbest;
            k = k+1;
            xb = x;
        else
            xa = x;
            x2 = x;
            x = X(N,:);
            Suii(k,1) = gbest;
            k = k+1;
            xb = x;
        end
        if gbest2 > gbest
            gbest = gbest2;
        end
        %タブーリストに追加
        T2 = T;
        for j = 1:bit
            if x(1,j) ~= x2(1,j)
                T2(TL+1,1) = j;
            else
            end
        end

        for t = 1:TL
            T(t,1) = T2(t+1,1);
        end
    
        
 end

 Gbest(m,1) = gbest;


end


HYOKA = HYOKA/50;
mean(Gbest),max(Gbest),min(Gbest),std(Gbest), k, HYOKA
