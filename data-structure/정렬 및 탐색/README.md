## 정렬 및 탐색
### [selection sort (선택 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/SelectionSort.cpp)  
**정렬되지 않은 정수들 중에서 가장 작은 값을 찾아서 정렬된 리스트 다음 자리에 놓는 정렬방법.**  
`1 10 5 8 7 6 4 3 2 9` 라는 정렬되지 않은 정수에서 가장 작은 값을 찾으면 1이다. 가장 앞으로 보낸다.  
1은 이미 가장 앞에 있으므로 정렬이 이루어졌다. 가장 앞의 1을 제외하고 가장 작은 값은 2인데, 1을 제외  
하고 가장 앞에 있는 원소 10과 바꾸면 `1 2 5 8 7 6 4 3 10 9`가 된다. 이후에 세번째로 가장 작은 값은 3  
인데 이 값을 5와 바꾸면 `1 2 3 8 7 6 4 5 10 9` 가 된다. 이러한 과정을 반복하면 끝까지 반복했을 때  
`1 2 3 4 5 6 7 8 9 10` 이라는 정렬된 정수 리스트를 얻을 수 있다.  
```c++
 for(int j=i;j<n;j++)
        {
            if(min>list[j])
            {
                min=list[j];
                index=j;
            }
        } // 가장 작은 원소를 찾아서 위치를 저장한다
temp=list[i];
        list[i]=list[index];
        list[index]=temp; // 두 원소의 위치를 바꾼다
```    
**💡선택 정렬의 시간 복잡도 : N(N+1)/2 => O(N^2)**   
### [bubble sort (버블 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/BubbleSort.cpp)
**옆에 있는 값과 비교해서 더 작은 값을 앞으로 보내는 정렬방법**  
`1 10 5 8 7 6 4 3 2 9` 라는 정렬되지 않은 정수에서 먼저 1과 10을 비교해서 더 작은 것을 앞으로 옮긴다.  
이미 1이 앞에 있으므로 그 다음 10과 5를 비교해서 더 작은 5를 앞으로 보내면 `1 5 10 8 7 6 4 3 2 9`이다.  
다음으로 10과 8을 비교해서 더 작은것을 앞으로 옮기면 `1 5 8 10 7 6 4 3 2 9` 이다. 그 다음으로 7과 10을  
비교해서 더 작은 7을 앞으로 옮기면 `1 5 8 7 10 6 4 3 2 9`이다. 이런식으로 한번의 반복이 끝났을때 리스트는  
`1 5 8 7 6 4 3 2 9 10` 인데, 가장 큰 값이 맨 뒤로 보내지는 방식이다. 10을 제외하고 1부터 9까지 앞의 방법  
을 이용해서 반복하면, 수행했을 때 결과는 가장 큰값이었던 9가 맨 뒤로 보내진 리스트를 얻게 된다. 끝까지   
반복하면  `1 2 3 4 5 6 7 8 9 10` 이라는 정렬된 리스트를 얻을 수 있다.  
```c++
for(j=0;j<9-i;j++) //뒤에서부터 집합의 크기 하나씩 감소
        {
            if(array[j]>array[j+1])
            {
                temp=array[j];
                array[j]=array[j+1];
                array[j+1]=temp;
            }
        }
```  
**💡버블 정렬의 시간 복잡도 : O(N^2)** 시간 복잡도는 선택 정렬과 동일하나 실제 수행 시간으로는 선택 정렬보다 훨씬  
느리다. 매번 교체를 해줘야 하는 점에서 실제로 더욱 비효율적이다.
### [insertion sort (삽입 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/InsertionSort.cpp)  
**각 숫자를 적절한 위치에 삽입하는 정렬방법**  
다른 정렬 방식들과 달리 삽입 정렬은 '필요할 때만' 위치를 바꾼다. `1 10 5 8 7 6 4 3 2 9` 라는 리스트에서, 1은 이미  
가장 앞에있어 삽입할 위치가 없어 내버려둔다. 10을 살펴보면, 10은 1의 앞과 뒤에 올 수 있는데,_ 1 _ 1보다 크므로 뒤  
쪽에 위치한다. 5는 앞을 봤을 때 들어갈 위치가 _ 1 _ 10 _ 이렇게 세 자리가 있는데, 가운데 위치에 들어간다. _ 1 5 10 _  
8은 _ 1 _ 5 _ 10 _ 중, 5와 10 사이에 들어가므로, 1 5 8 10 이렇게 정렬된 리스트가 반환된다. 이런 식으로 반복하면,  
정렬된 리스트를 얻을 수 있다. 앞의 원소들이 이미 정렬되어 있기 때문에 위치를 서로 바꿔주기만 하면 되므로 전체를  
다 살펴볼 필요가 없다. 
```c++
while(array[j]>array[j+1])
         {
             temp=array[j];
             array[j]=array[j+1];
             array[j+1]=temp;
             /* 옆에있는것과 비교, 하나씩 내려가면서 
             옆 원소가 더 크다면 바꿔준다*/
             j--; 
             if(j<0)
                break; 
         }
```  
**💡삽입 정렬의 시간 복잡도 : O(N^2)** 필요할 때만 삽입을 진행하므로 **데이터가 정렬된 상태에서는 어떤 알고리즘보다 빠르다는**  
특징을 가진다.  
### [quick sort (퀵 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/QuickSort.cpp)
**대표적인 '분할 정복'알고리즘을 활용한 정렬방법**  
특정한 값(기준값=Pivot) 기준으로 큰 숫자와 작은 숫자의 집합으로 나누는 방법. 보통 첫번째 원소를 피벗으로 지정한다.  
`(3) 7 8 1 5 9 6 10 2 4` 라는 리스트에서 첫번째 원소 3을 피벗으로 지정한다. 왼쪽에서 오른쪽으로 이동하며 검사를 할 때는,  
3보다 큰 값을 선택한다. 따라서 7을 선택한다. 오른쪽에서 왼쪽으로 검사할 때는 3보다 작은 값을 선택한다. 따라서 2를 선택한다.  
그 이후에 큰 값과 작은 값을 서로 바꾸어준다. `(3) 2 8 1 5 9 6 10 7 4` 이 상황에서 이전처럼 3보다 큰 값인 8을 선택하고,  
작은 값인 1을 선택해서 위치를 바꾸어준다. `(3) 2 1 8 5 9 6 10 7 4` 마찬가지로 pivot을 고정한 채 큰 값 8과 작은 값 1이  
구해지는데 8과 1은 서로 **엇갈린다.즉, 작은 값의 인덱스가 큰 값의 인덱스보다 더 작다.** 이런 상황에서는 왼쪽에 있는 값  
과 3을 서로 바꿔준다. `1 2 (3) 8 5 9 6 10 7 4` 이런식으로 하면 3왼쪽은 3보다 작은 값들이, 3 오른쪽에는 3보다 큰 값  
이 위치해서 `1 2`라는 기준값 3보다 작은 리스트와 `8 5 9 6 10 7 4` 기준값 3보다 큰 리스트로 분할된 것을 알 수 있다.  
3보다 작은 리스트에서는 1을 기준값으로 해서, `(1) 2` 3보다 큰 리스트에서는 8을 기준값으로 해서 `(8) 5 9 6 10 7 4`  
또 정렬을 수행한다. 이런식으로 퀵 정렬을 반복하면, `1 2 3 4 5 6 7 8 9 10` 이라는 정렬된 리스트를 얻을 수 있다.  
```c++
 while(i<=j) //엇갈릴 때 까지 반복 . 왼쪽 값과 pivot 값을 바꾼다
    {
        while(i<=end && data[i]<=data[key]) //키 값보다 큰 값을 만날때까지
        {
            i++;
        }
        while(data[j]>=data[key] && j>start) //키 값보다 작은 값을 만날때까지 
        {
            j--; 
        }
        if(i>j) //엇갈린 상태면 키값과 교체
        {
            temp=data[j];
            data[j]=data[key];
            data[key]=temp;
        }
        else{ //엇갈리지 않았다면 두개의 값 교체
            temp=data[j];
            data[j]=data[i];
            data[i]=temp;
        }
    }

```  
**💡퀵 정렬의 시간 복잡도 : O(N×logN)**  
`1 2 3 4 5 6 7 8 9 10`을 정렬한다고 하면, 원소의 수가 10개일 때 선택 정렬을 이용하면 10×10=100 이지만 퀵 정렬은 분할 정렬이므로     
`1 2 3 4 5` 와 `6 7 8 9 10`으로 분할한 뒤 5×5=25 연산을 2번 수행하므로 훨씬 빠르다.   
**💡퀵 정렬의 최악 시간 복잡도 : O(N^2)**  
이미 정렬이 되어있는 경우, 분할 정복의 이점을 사용하지 못해 실행시간이 느려진다.  
### [merge sort (병합 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/MergeSort.cpp)
**일단 정확히 반으로 나누고 나중에 정렬하는 방법**  
항상 반으로 쪼개기 때문에 pivot 값이 없다. 병합 정렬의 시간복잡도는 **N×logN**인데, 항상 반으로 쪼개는 특징이 시간복잡도가 logN이 되도록  
만들어준다. `7 6 5 8 3 5 9 1`이라는 배열을 병합 정렬을 이용해서 정렬한다고 하면, 시작 상태는 계속 반으로 나눠서 전부다 한개씩 남을 때 까지    
나눈 상태이다. 합칠 때는 기본적으로 2의 배수만큼 합친다. 7과 6을 정렬해서 `6 7`을 만들고, 5와 8을 정렬해서 `5 8`을 만들고, 3과 5를 정렬해서  
`3 5`를 만들고, 9 1을 정렬해서 `1 9`를 만든다. 정렬이 되었지만 두 개의 배열 안에서만 정렬이 되었다. 그 다음 단계에서는 `6 7`과 `5 8`을 비교  
해서 정렬을 수행한다. `5 6 7 8` 이 만들어진다. 마찬가지로 `3 5`와 `1 9`를 합친 후 정렬해서 `1 3 5 9`가 만들어진다. 마지막으로 두 배열을  
합쳐서 결과적으로 `1 3 5 5 6 7 8 9`를 만든다. **배열의 너비는 원소의 개수 N이고, 높이는 3이다. log<sub>2</sub>8=3 
이기 때문이다. 아주 작은 단계  만 수행하더라도 전체 데이터의 확인이 가능하다. 중요한 점은 **합치는 순간에 정렬을 한다는 점이다** 
```c++
 // 작은 순서대로 배열에 삽입
    while(i<=middle &j<=n)
    {
        if(a[i]<=a[j])
        {
            sorted[k]=a[i];
            i++;
        }
        else
        {
            sorted[k]=a[j];
            j++;
        }
        k++;
    }
    //남은 데이터 삽입
    if(i>middle)
    {
        for(int t=j;t<=n;t++)
        {
            sorted[k]=a[t];
            k++;
        }
        
    }
    else
    {
        for(int t=i;t<=n;t++)
        {
            sorted[k]=a[t];
            k++;
        }
    }
    //정렬된 배열을 삽입
    for(int t=m;t<=n;t++)
    {
        a[t]=sorted[t];
    }
```  
**💡병합 정렬의 시간 복잡도 : O(N×logN)** 병합 정렬의 또다른 특징으로는, 기존의 데이터를 담은 추가적인 배열 공간  
이 필요하다는 점에서 메모리 활용이 비효율적이라는 문제가 있다.    
### [heap sort (힙 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/HeapSort.cpp)  
**힙 트리 구조를 이용하는 정렬 방법**  
힙 정렬을 이해하기 위해서는, 이진 트리와 완전 이진 트리에 대한 이해가 필요하다.  
이진 트리는 모든 노드의 자식 노드가 2개 이하인 트리 구조를, 완전 이진 트리는 루트 노드부터 시작해서 자식 노드가 왼쪽  
자식 노드, 오른쪽 자식 노드로 차근차근 들어가는 구조의 이진 트리이다.  
![이진 트리](https://github.com/euichanhwang/CS_study/blob/main/img/%EC%9D%B4%EC%A7%84%20%ED%8A%B8%EB%A6%AC.jpg)
![완전 이진 트리](https://github.com/euichanhwang/CS_study/blob/main/img/%EC%99%84%EC%A0%84%20%EC%9D%B4%EC%A7%84%20%ED%8A%B8%EB%A6%AC.jpg)
 **힙**(heap)은 최소값이나 최댓값을 빠르게 찾아 내기 위해 완전 이진 트리를 기반으로 하는 트리이다.  
힙에는 최대 힙과 최소 힙이 존재하는데 최대 힙은 부모 노드가 자식 노드보다 큰 힙이라고 할 수 있다.  
즉, 더 큰 값이 위로(부모가) 간다(된다).힙 정렬을 하기 위해서는 정해진 데이터를 힙 구조를 가지도록 만들어야 한다.  
힙 정렬을 수행하기 위해서, **힙 생성 알고리즘**(heapify algorithm)을 사용하는데, 어떠한 노드에 대해서 최대 힙이 붕괴되었을  
시 부모 노드와 부모 노드보다 더 큰 자식 노드를 교체한다. 위치를 바꾼 후에도 자식이 존재 하는 경우 또 자식 중에서 더 큰 자식  
과 부모 노드의 위치를 바꾼다. 한번 힙 생성 알고리즘이 수행되는 시간은 트리의 높이와 같다. 
![힙 구조와 힙 생성 알고리즘](https://github.com/euichanhwang/CS_study/blob/main/img/%ED%9E%99%20%EA%B5%AC%EC%A1%B0%EC%99%80%20%ED%9E%99%20%EC%83%9D%EC%84%B1%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98.jpg)  
힙 생성 알고리즘은, 전체 트리에 대해서 heapify를 반복적으로 수행하면 전체 노드가 다 힙 구조가 된다. 힙 생성 알고리즘의 시간 복잡도는  
한 번 자식 노드로 내려갈 때마다 노드의 개수가 2배로 증가한다는 점에서 O(log<sub>2</sub>N)이다.
![힙 정렬 진행과정](https://github.com/euichanhwang/CS_study/blob/main/img/%ED%9E%99%20%EA%B5%AC%EC%A1%B0%EC%9D%98%20%EC%A7%84%ED%96%89%EA%B3%BC%EC%A0%95.jpg)  
```c++
// 전체 트리 구조를 최대 힙 구조로 만든다.
    for(int i=1;i<number;i++)
    {
        int c=i;
        do{
            int root=(c-1)/2; //자기 자신의 부모를 의미
            if(heap[root]<heap[c])
            {
                int temp=heap[root];
                heap[root]=heap[c];
                heap[c]=temp;
            }
            c=root;
        }while(c!=0);
    }
    //크기 줄이면서 반복적으로 힙 구성
    for(int i=number-1;i>=0;i--)
    {
        int temp=heap[0]; //0번째 인덱스가 제일 큰 값
        heap[0]=heap[i];
        heap[i]=temp;
        int root=0;
        int c=1;
        do{
            c=2*root+1;
            //자식 중에 더 큰값을 찾기
            if(heap[c]<heap[c+1]&&c<i-1)
            {
                c++;
            }
            //루트보다 자식이 더 크다면 교환
            if(heap[root]<heap[c]&&c<i)
            {
                int temp=heap[root];
                heap[root]=heap[c];
                heap[c]=temp;
            }
            root=c;
        }while(c<i);
```  
**💡힙 정렬의 시간 복잡도 : N×log<sub>2</sub>N**  
한 번 자식 노드로 내려갈 때마다 노드의 개수가 2배씩 증가한다는 점에서 log<sub>2</sub>N이다.여기에 정점의 수 N을 곱해준다.    
### [counting sort (계수 정렬)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/CountingSort.cpp)  
**크기를 기준으로 개수를 세는 정렬 방법**    
**범위 조건** 이 있는 경우에 한해서 굉장히 빠른 정렬 방법이다. 위치를 바꿀 필요가 없이 크기를 기준으로 개수를 센다.  
5이하의 자연수 데이터 `1 3 2 4 3 2 5 3 1 2 3 4 4 3 5 1 2 3 5 2 3 1 4 3 5 1 2 1 1 1`를 오름차순으로 정렬할 때,  
첫번째 1을 확인 한 후 크기가 1인 데이터를 1 증가시킨다. 두번째 3을 확인한 후 크기가 3인 경우 데이터를 1 증가시킨다.   
그 다음 세번째 2를 확인 한 후 크기가 2인 데이터를 1 증가시킨다.즉, 크기를 기준으로 해서 한개씩 데이터를 증가시킨다.  
하나를 확인 할 때 마다 배열의 데이터를 하나씩 증가시켜주는 방식이라고 할 수 있다. 마지막으로, 크기 1부터 5까지 해당  
숫자만큼 출력하면 된다.
```c++
 int arr[30]={
        1,3,2,4,3,2,5,3,1,2,
        3,4,4,3,5,1,2,3,5,2,
        3,1,4,3,5,1,2,1,1,1
    };
    for(int i=0;i<5;i++)
    {
        count[i]=0;
    }
    for(int i=0;i<30;i++)
    {
        count[arr[i]-1]++;
    }
     for(int i=0;i<5;i++)
     {
         if(count[i]!=0)
         {
             for(int j=0;j<count[i];j++) //count[i] 만큼 출력
                cout << i+1 << " ";
         }
     }
```
**💡계수 정렬의 시간 복잡도 : O(N) (단,데이터의 크기가 한정되어 있을 때)**
앞에서 차례대로 데이터를 하나씩 읽어들이기 때문에 정렬 자체에 필요한 시간 복잡도는 O(N)이다.

### std::sort 함수 사용하기  
**stl 라이브러리에 포함된 sort 함수를 이용해서 정렬하는 방법.** 
```c++
int a[10]={9,3,5,4,1,10,8,6,7,2};
    sort(a,a+10); //10은 개수의 의미에 가깝다. 원소가 10개 있다고 보면 된다.
```  
내림차순 정렬을 위해, 함수를 선언한 후 sort 함수의 argument로 포함시켜서 구현 가능하다.  
또한,마지막 argument로 **greater<타입이름>()** 를 추가하면 내림차순 정렬이 가능하다.  
```c++
bool compare(int a,int b)
{
    return a>b; //내림차순 정렬
}
sort(a,a+10,compare);
```
클래스를 이용한 객체의 멤버 변수를 정렬할 때도 사용 가능하다.
```c++
class Student
{
public:
    string name;
    int score;
    Student(string name,int score)
    {
        this->name=name;
        this->score=score;
    }
    //정렬 기준은 '점수가 적은 순서'
    bool operator < (Student &student)
    {
        return this->score <student.score;
    }

};
```  

### [binary search (이진 탐색)](https://github.com/euichanhwang/CS_study/blob/main/data-structure/%EC%A0%95%EB%A0%AC%20%EB%B0%8F%20%ED%83%90%EC%83%89/BinarySearch.cpp)  
**오름차순으로 정렬된 정수의 리스트를 같은 크기의 두 부분 리스트로 나누고 필요한 부분에서만**    
**탐색하도록 제한하여 원하는 원소를 찾는 알고리즘.**  
- middle(중간값)을 (left+right)/2로 선언한다. left=0, right=n-1 이다.(각각 리스트의 왼쪽,오른쪽 끝 지점)      
- a[middle]과 key값을 비교해서 세 가지 경우 중 하나를 고려한다.
    1. key<a[middle] : 이 경우 key가 존재한다면 그것은 0과 middle 사이에 있으므로 right를 middle-1로 설정한다.  
    2. key=a[middle] : 이 경우에는 middle을 반환한다.  
    3. key>a[middle] : 이 경우 key가 존재한다면 middle+1과 n-1 사이에 있으므로 left를 middle+1로 설정한다.

**x가 발견되지 않고 검사할 정수가 남아 있다면 middle을 다시 계산하고 탐색을 계속한다.**  
```c++
int BinarySearch(int *list, const int key, const int n)
{
  int left = 0;
  int right = n - 1;
  while (left <= right)  //원소가 더 있는 한
  {
    int middle = (left + right) / 2;
    if (key < list[middle])
      right = middle - 1;
    else if (key > list[middle]) left=middle+1;
      else return middle;
  }
  return -1; // not found
}
```  
---