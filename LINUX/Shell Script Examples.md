# Shell Script 파일 


### 예제 1
 2020.11.17 
```
#!/bin/bash 
# 주어진 자연수의 총합, 평균, 최대값을 출력하는 shell program을 작성하라 (각각의 함수로 구현해라)
sum=0; avg=0; max=0; num=$#; 
if [ $# -eq 0 ]
then 
    echo "Usage: $0 n1 n2 ... " 
    exit 1
fi
function fsum {
    for i in $@
    do 
        let sum = $sum + $i
    done
}
function favg {
    let avg $sum/$num
}

function fmax{
    for i in $@
    do
        if [ i -gt max ] 
        then 
            max = $i
        fi
    done
}

fsum $@
favg
fmax $@
echo "Sum = $sum"
echo "Average = $avg"
echo "Max = $max"
```

### 예제 2
```
#!/bin/bash 

# factorial을 계산하는 쉘 프로그램을 작성해라. 재귀적 (recursive) 함수 호출을 사용하시오

function fact {
    local x=$1
    let local y=$x-1
    local z=1

    if [ $x -gt 1 ] 
    then 
        fact $x
        let z=$x*$?
    fi 
    return $z
}
```
