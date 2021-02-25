## fibbinocci number at an index

def fibbinoci(n):
    
    current_num = 1
    prev_num = 1
    result = 0
    k = 3
    
    if n <= 0:
        print("n is negative")
    elif type(1) != int:
        print("n should be numeric")
    elif (n == 1) or (n == 2):
         print(1)
    else:
        
        while(k<=n):
            
            result = current_num + prev_num
            prev_num = current_num
            current_num = result
            
            k = k+1
        print(current_num)
