### �����㷨

<hr>



#### 1�������㷨����



##### 1�����õĲ����㷨

˳����ң����Բ��ң�

���ֲ��ң��۰���ң�

��ֵ����

쳲���������





##### 2�����Բ����㷨

���Բ��Ҵ��룺

```java
//���Բ���
public static seqSearch (int[] arr,int value){
    for(int i = 0; i < arr.length; i++){
        if(arr[i] == value){
            return i;
        }
    }
    return -1;
}
```



##### 3�����ֲ����㷨

�Ƚ������Ϊ�������飬Ȼ����в���



˼·������

��1������ȷ����������м��±�

��2��Ȼ������Ҫ���ҵ��������м�ֵ�Ƚϣ�Ȼ����ݱȽϽ��еݹ飬�������ıߵݹ飬�����Ⱦͷ���

��3�������ݹ��������ҵ������ݹ飬�Ҳ���Ҳ�����ݹ�



�򵥶��ֲ���

```java
 //δ�Ż����ֲ��ҷ�
public static int binarySearchOne (int[] arr,int left,int right,int value){
        //������Ҵ󣬷���-1��ʾû�ҵ�
        if(left > right){
            return -1;
        }
        int mid = (left+right)/2;
        int midValue = arr[mid];
        if(value < midValue){
            //û�ҵ�mid-1�ᵽ-1
            return binarySearchOne(arr,left,mid - 1,value);
        }else if(value > midValue){
            //û�ҵ���mid+1�ᵽarr.length�����
            return binarySearchOne(arr,mid+1,right,value);
        }else{
            return mid;
        }
    }
}
```



���ֲ�����������

˼·������

1.�ҵ�midֵ��Ҫ�������أ���

2.��mid����ֵ�����ɨ�裬�����������Ԫ�ص��±���뵽����

3.2.��mid����ֵ���ұ�ɨ�裬�����������Ԫ�ص��±���뵽����

```java
 //�Ż����ֲ��ҷ����ҵ�������ֵͬ
public static ArrayList<Integer> binarySearchAll (int[] arr,int left,int right,int value){
        //������Ҵ󣬷��ؿյļ��ϱ�ʾû�ҵ�
        if(left > right){
            return new ArrayList<Integer>();
        }
        int mid = (left+right)/2;
        int midValue = arr[mid];
        if(value < midValue){
            //û�ҵ�mid-1�ᵽ-1
            return binarySearchAll(arr,left,mid - 1,value);
        }else if(value > midValue){
            //û�ҵ���mid+1�ᵽarr.length�����
            return binarySearchAll(arr,mid+1,right,value);
        }else{
            List<Integer> resIndexList = new ArrayList<>();
            //����߽��в���
            int temp = mid - 1;
            while(true){
                //��Ϊ������ģ�������ֵֻͬ����������
                if(temp < 0 || arr[temp] != value){
                    break;
                }
                resIndexList.add(arr[temp]);
                temp--;
            }
            //���ұ߽��в���
            int temp = mid + 1;
            while(true){
                //��Ϊ������ģ�������ֵֻͬ����������
                if(temp > arr.length - 1 || arr[temp] != value){
                    break;
                }
                resIndexList.add(arr[temp]);
                temp++;
            }
            return resIndexList;
        }
    }
}
```



##### 4����ֵ�����㷨

ԭ����ֵ�����㷨�����ڶ��ֲ��ң���ͬ���ǲ�ֵ����ÿ�δ�����Ӧmid����ʼ���ң������ֲ��ҵ���mid��ʽ

��1��left��ʾ���������right��ʾ�ұ�������valueΪ����ֵ

��2��mid = arr[left] + (right -  left) *(value - arr[left]) /  (arr[right] - a[left])



��ֵ���ҵ�ʹ�ó�����

�����������ϴ󣬹ؼ��ֲַ��Ͼ��ȵò��ұ���˵�����ò�ֵ���ҽϿ죻�ؼ��ֲַ������ȣ������������ϴ󣬲�һ���ȶ��ֲ��Һ�



��ֵ�����㷨����

```java
public static void insertSearch (int[] arr,left,right,value){
    //��ֹmidֵ��������Խ�磬�жϱ�����
    if(left > right || value < arr[0] || value > arr[arr.length-1]){
        return -1;
    }
    int mid = (value - arr[left])/(arr[right]-arr[left])*(right-left);
    int midValue = arr[mid];
    if(value > midValue){
        return insertSearch(arr,mid+1,right,value);
    }else if(value < midValue){
        return insertSearch(arr,left,mid-1,value);
    }else{
        return mid;
    }
}
```



##### 5��쳲����������㷨

쳲����������㷨��Ҳ�лƽ�ָ��㷨

ԭ����ǰ�������ƣ������ı����м�ڵ��λ�ã��м�ֵ��������ֵ���ֵ�õ�������λ�ڻƽ�ָ�㸽��

`mid = left + F(k-1) - 1`



F(k-1) - 1����⣺

��1����쳲���������F(k) - 1 = (F(k-2) - 1) + (F(k-1) - 1) + 1����ʽ˵����ֻҪ˳���ĳ���ΪF(k) - 1������Խ��ñ�ֳɳ���ΪF(k-2) - 1��F(k-1) - 1���Σ��Ӷ��м�λ����mid = low + F(k-1) - 1

��2�����Ƶ�ÿһ���Ӷο��Բ�����ͬ��ʽ�ָ�

��3����˳�����n��һ���պõ���F(k) - 1������kֵֻҪ��ʹ��F(k)-1ǡ�ô��ڻ����n���ɣ������´���õ���˳��������Ӻ�������λ�ã���n+1��F(k)-1λ�ã�������ֵΪnλ�õ�ֵ����



��ʽ�Ƶ�ͼ��

![](�㷨img/�ƽ�ָʽ.png)





쳲���������

```java
public static fibonacciSearch (int[] arr,int value){
    int low = 0;
    int high = a.length - 1;
    int k = 0;//쳲������ָ���ֵ�±�
    int mid = 0;//��ŷָ�㴦��ֵ
    int[] fiboArr = getFibonacciArray(20);
    
    //��ȡ�ָ���ֵ�±�
    while(high > f[k] - 1){
        k++;
    }
    
    //������ʱ����
    int[] temp = Arrays.copyOf(arr,f[k]);
    
    //f[k]��ֵ������ڵ������鳤�ȣ�����ĵط��Ჹ0
    //�����ಿ�ֽ��д���������ʼ�ձ�������
    for(int i = high + 1;i < temp.length;i++){
        temp[i] = a[high];
    }
    
    //ʹ��whileѭ�����ҵ�����Ҫ���ҵ�valueֵ
    while(low <= high){
        mid = low + fiboArr[k-1] - 1;
        //�������
        if(key < temp[mid]){
            high = mid - 1;
            k--;
        }else if(key > temp[mid]){
            low = mid + 1;
            //��Ϊ����ĳ�ʼ������f[k-2],��f[k-2]Ϊ�ָ��
            k -= 2;
        }else{
            //���ݴ�С������������
            return mid <= high ? mid : high;
        }
        return -1;
    }
}

//����һ��쳲���������
public static int[] getFibonacciArray (int maxSize){
    int[] fArr = new int[maxSize];
    f[0] = 1;
    f[1] = 1;
    for(int i = 2;i < maxSize;i++){
        arr[i] = arr[i-1] + arr[i-2];
    }
    return arr;
}
```



#### 2����ϣ��ɢ�б�

��ϣ��

��ϣ��Ҳ��ɢ�б����ݹؼ���ֵ��ֱ�ӽ��з��ʵ����ݽṹ��ͨ�����ؼ���ֵӳ�䵽����һ��λ�������ʼ�¼���Լӿ�����ٶȡ�ʹ�õ�ӳ�亯�����ǽ���ɢ�к�������ż�¼���������ɢ�б�



ʵ����ʹ�û���㽫�������ݴ浽���棬�ܵ������ж�ȡ���Ͳ�ȥ��ȡ���ݿ����ݡ�

������Ʒ��Redis��Memcache����Ҫ����ͨ�������������ݽṹʵ�ֵģ�

��1����ϣ������+���� 

��2������+������



��ϣ����Ҫ���þ���������



�ȸ��ϻ��⣺

ʵ������ÿ�쵱����Ա��������ʱ��Ҫ�󽫸�Ա������Ϣ���루id���Ա����䣬סַ�����������Ա����idʱ��Ҫ����ҵ���Ա��������Ϣ��

Ҫ�󣺲��������ݿ⣬������ʡ�ڴ棬�ٶ�Խ��Խ��

˼·������ʹ�ù�ϣ���������Ա��Ϣ



��Ա��

```java
class Emp {
    private int id;
    private String name;
    private String address;
    Emp next;
    public Emp (int id,String name,String address){
        this.id = id;
        this.name = name;
        this.address = address;
    }
}
```

ɢ�б�

```java
public class HashTableDemo {
    //���������������
    private EmpLinketList[] empListArray;
    private int size;
    
    //��ʼ������
    public HashTableDemo (int size){
        this.size = size;
        empListArray = new EmpLinketList[size];
        for(int i = 0; i < size; i++){
            empListArray[i] = new EmpLinkedList();
        }
    }
    //��ӹ�Ա
    public void add (Emp emp) {
        int hash = getHash(emp.getId);
        empListArray[hash].add(emp);
    }
    
    //����ɢ�б�
    public void list () {
        for(int i = 0; i < size; i++){
            empListArray[i].list();
        }
    }
    
    //����id��ȡ��ϣ
    public int getHash (int id){
        return id % size;
    }
}

class EmpLinkedList {
    private Emp head;
    
    //���
    public void add (Emp emp){
        if(head == null){
            head = emp;
            return;
        }
        Emp tempEmp = head;
        while(tempEmp.next != null){
            tempEmp = tempEmp.next;
        }
        tempEmp.next = emp;
    }
    
    //����
    public void list (){
        if(head == null){
            System.out.println("list is empty.");
            return;
        }
        Emp tempEmp = head;
        while(true){
            System.out.printf("id=%d,name=%s\n",tempEmp.getId(),tempEmp.getName());
            if(tempEmp.next == null){
             	break;   
            }
            tempEmp = tempEmp.next;
        }
    }
}
```



#### 3�����ṹ

##### 1��Ϊʲô��Ҫ���������ݽṹ

+ ����
  - �ŵ㣺����Ԫ���ٶȿ죬����Ԫ�ؿ���ͨ�������㷨��������Ч�ʣ�����Ч�ʸ�
  - ȱ�㣺���Ҿ���ֵʱ�����߲���ֵ��Ч�ʽϵ�

+ ��ʽ�洢
  - �ŵ㣺�ʺϲ��룬ɾ��Ч��Ҳ�ܺ�
  - ȱ�㣺����Ч�ʵ�

+ ���Ĵ洢��ʽ
  - �ŵ㣺������ݴ洢����ȡЧ�ʣ�����������������ȿ��Ա�֤���ݲ����ٶȣ�ͬʱ���Ա�֤���ݵĲ��롢ɾ�����޸��ٶ�



����������ԭ��ͼ��

![](�㷨img/����������.jpg)



##### 2�����ĳ�������



###### 1���������ڽ���

��1���ڵ�

��2�����ڵ�

��3���ӽڵ�

��4�����ڵ�

��5��Ҷ�ӽڵ㣺û���ӽڵ�Ľڵ�

��6���ڵ��Ȩ���ڵ�ֵ��

��7���ڵ��·�����ҵ��ýڵ��·�ߣ�

��8����

��9������

��10�����ĸ߶ȣ�������������

��11��ɭ�֣������������ɭ�֣�

�ڵ��������ͼ��

![](�㷨img/�ڵ�����.jpg)



###### 2���������ĸ���

��1��ÿ���ڵ�����ֻ���������ӽڵ��һ����ʽ����

��2���������Ľڵ��Ϊ**��ڵ�**��**�ҽڵ�**

��3�����������������Ҷ�ӽڵ㶼�����һ�㣨n���������ܽڵ���Ϊ`2^n-1`�����ǳ�֮Ϊ**��������**

��4�����������������Ҷ�ӽڵ㶼�����һ�㣬���ߵ����ڶ��㣬���������һ���Ҷ�ӽڵ�����������������ڶ����Ҷ�ӽڵ����ұ����������ǳ�֮Ϊ**��ȫ������**



�������ı�����

��1��ǰ�����

��2���������

��3���������

���ݸ��ڵ�����λ���ж�����һ�ֱ�������



�����������ķ�����

��1������һ�ö�����

��2��ǰ��������������ǰ�ڵ㣬������ӽڵ㲻Ϊ�գ���ݹ����ǰ�������������ӽڵ㲻Ϊ�գ���ݹ����ǰ�����

��3����������������ǰ�ڵ�����ӽڵ㲻Ϊ�գ���ݹ���������������ǰ�ڵ㣻�����ǰ�����ӽڵ㲻Ϊ�գ���ݹ��������

��4����������������ǰ�ڵ�����ӽڵ㲻Ϊ�գ���ݹ��������������ǰ�ڵ�����ӽڵ㲻Ϊ�գ���ݹ��������������ǰ�ڵ�



###### 3��ǰ�����

��������ڵ㣬�ڱ�����������������

```java
public class BinaryTree {
    private PersonNode root;
    
    public void setRoot(PersonNode root){
        this.root = root;
    }
    
    //ǰ�����
    public void preOrder () {
        if(this.root != null){
            this.root.preOrder();
        }else{
            System.out.println("tree is empty.");
        }
    }
    
    //�������
    public void infixOrder {
        if(this.root != null){
            this.root.infixOrder();
        }else{
            System.out.println("tree is empty.");
        }
    }
    
    //�������
    public void postOrder (){
        if(this.root != null){
            this.root.postOrder();
        }else{
            System.out.println("tree is empty.");
        }
    }   
}

class PersonNode {
    private int no;
    private String name;
    private PersonNode left;
    private PersonNode right;
    
    public PersonNode (int no,String name){
        this.no = no;
        this.name = name;
    }
    
    //getter,setter,toString
    public void setLeft(){}
    public void setRight(){}
    
    //ǰ�����
    public void preOrder (){
        System.out.println(this);
        //�ݹ���������ǰ�����
        if(this.left != null){
            this.left.preOrder();
        }
        //�ݹ�������������
        if(this.right != null){
            this.right.preOrder();
        }
    }
    
    //�������
    public void infixOrder (){
        //���������������
        if(this.left != null){
            this.left.infixOrder();
        }
        //������ڵ�
        System.out.println(this);
        //���������������
        if(this.right != null){
            this.right.infixOrder();
        }
    }
    
    //�������
    public void postOrder () {
         //���������������
        if(this.left != null){
            this.left.postOrder();
        }
        //���������������
        if(this.right != null){
            this.right.postOrder();
        }
        //������ڵ�
        System.out.println(this);
    }
}
```





###### 4���������

�ȱ�������������������ڵ㣬�ڱ����������������ϣ�



###### 5���������

�ȱ������������ڱ��������������������ڵ㣨�����ϣ�



###### 6�����������ҽڵ�

��1��ǰ�����

˼·������

+ ���жϵ�ǰ�ڵ��no�Ƿ���ڲ��ҵģ������ȣ����ص�ǰ�ڵ�

+ �����ж����ӽڵ��Ƿ�Ϊ�գ���Ϊ�գ���ݹ�ǰ�����
+ ���ӽڵ�û���ҵ���ȵģ�����ҽڵ㿪ʼǰ�����

```java
public PersonNode preOrderSearch (int no){
    //��ǰ�ڵ�Ƚ�
    if(this.no == no){
        return this;
    }
    PersonNode temp = null;
    
    //������ǰ�����
    if(this.left != null){
        temp = this.left.preOrderSearch(no);
    }
    if(temp != null){
        return temp;
    }
    
    //������ǰ�����
    if(this.right != null){
        temp = this.right.preOrderSearch(no);
    }
    if(temp != null){
        return temp;
    }
    
    return temp;
}
```





��2���������

˼·������

+ �жϵ�ǰ���ӽڵ��Ƿ�Ϊ�գ���������ݹ��������
+ ���û���ҵ��뵱ǰ�ڵ�Ƚϣ�û�ҵ������������������

```java
public infixOrderSearch (int no) {
    //�������������
    PersonNode temp = null;
    if(this.left != null){
        temp = this.left.infixOrderSearch(no);
    }
    if(temp != null){
        return temp;
    }
    
    //��ǰ�ڵ�Ƚ�
    if(this.no == no){
        return this;
    }
    
    //�������������
    if(this.right != null){
        temp = this.right.infixOrderSearch(no);
    }
    if(temp != null){
        return temp;
    }
    
    return temp;
}
```





��3���������

˼·������

+ �жϵ�ǰ�ڵ����ӽڵ��Ƿ�Ϊ�գ������Ϊ�գ�����ݹ��������
+ ���û�ҵ����������ұߵݹ������ң�����û�ҵ�
+ ����ڵ�Ƚ�

```java
public PersonNode postOrderSearch(int no){
    PersonNode temp = null;
    //�������������
    if(this.left != null){
        temp = this.left.postOrderSearch(no);
    }
    if(temp != null){
        return temp;
    }
    
    //�������������
    if(this.right != null){
        temp = this.right.postOrderSearch(no);
    }
    if(temp != null){
        return temp;
    }
    
    //��ǰ�ڵ�Ƚ�
    if(this.no == no){
        return this;
    }
    
    return temp;
}
```



###### 7�����ֱ�����ʽ�ıȽ�

