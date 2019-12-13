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

//����Ҫ�ݹ�Ķ��ֲ���
public class BinarySearch {

    public static int binarySearch (int[] arr,int value){
        int mid = 0;
        int left = 0;
        int right = arr.length - 1;
        //С�ڵ��ڣ�ֻ��һ����ʱ��Ҫ�ж�
        while(left <= right){
            //ֱ��left + right������Խ��
            mid = left + (right - left) / 2;
            if(arr[mid] > value){
                right = mid - 1;
            }else if(arr[mid] < value){
                left = mid + 1;
            }else if(arr[mid] == value){
                return mid;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        //���Դ���
        int[] arr = {1,3,5,12,15,19};
        System.out.println(binarySearch(arr,1));
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
    //Ԥ������
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
    while(high > fiboArr[k] - 1){
        k++;
    }
    
    //������ʱ����
    int[] temp = Arrays.copyOf(arr,fiboArr[k]);
    
    //f[k]��ֵ������ڵ������鳤�ȣ�����ĵط��Ჹ0
    //�����ಿ�ֽ��д���������ʼ�ձ�������
    for(int i = high + 1;i < temp.length;i++){
        temp[i] = a[high];
    }
    
    //ʹ��whileѭ�����ҵ�����Ҫ���ҵ�valueֵ
    while(low <= high){
        mid = low + fiboArr[k-1] - 1;
        //�������
        if(value < temp[mid]){
            high = mid - 1;
            k--;
        }else if(value > temp[mid]){
            low = mid + 1;
            //��Ϊ����ĳ�ʼ������f[k-2],��f[k-2]Ϊ�ָ��
            k -= 2;
        }else{
            //���ݴ�С������������
            return mid <= high ? mid : high;
        }
    }
    return -1;
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
        int hash = getHash(emp.getId());
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
class Emp {}//ʡ��
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



##### 3���������ĸ���

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



###### 1��ǰ�����

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





###### 2���������

�ȱ�������������������ڵ㣬�ڱ����������������ϣ�



###### 3���������

�ȱ������������ڱ��������������������ڵ㣨�����ϣ�



###### 4�����������ҽڵ�

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



###### 5��������ɾ���ڵ�

�޹��������ɾ���ڵ�

�涨��

��1�����ɾ������Ҷ�ӽڵ㣬��ɾ���ýڵ�

��2�����ɾ���Ľڵ��Ƿ�Ҷ�ӽڵ㣬��ɾ��������

˼·��

��1����Ϊ�������ǵ���ģ��������ǱȽϵĵ�ǰ�Ľڵ�����ӽڵ�����ӽڵ�

��2�����root�ڵ㲻Ϊ�գ���ֵ�ͺͲ���ֵ��ȣ��������ÿ�

��3������root�ڵ�ִ�������ɾ������

��4������ɾ�������������ӽڵ��������ֵ�жϣ������ȣ���ֹ����

��5����߲��ȣ������ӽڵ��ж�ֵ�������ȣ���ֹ����

��6�������ȣ�������ӽڵ㲻Ϊ�գ�ִ�����ӽڵ��ɾ������

��7������û�ҵ���������ӽڵ㲻Ϊ�գ�ִ�����ӽڵ��ɾ������

��8��һֱû�ҵ��������



�ݹ�ɾ���ڵ�

```java
//PersonNodeɾ������
public PersonNode delete (int num){
        //ע�⵱ǰ�ڵ���ж���ͨ�����ڵ���бȽϵģ����Բ��ÿ���
        PersonNode result = null;

        //�ж����ӽڵ�ֵ�Ƿ����
        if(this.left != null && this.left.getNum() == num){
            result = this.left;
            this.left = null;
            return result;
        }

        //�ж����ӽڵ�ֵ�Ƿ����
        if(this.right != null && this.right.getNum() == num){
            result = this.right;
            this.right = null;
            return result;
        }

        //�ݹ����ӽڵ�ɾ������
        if(this.left != null){
            result = this.left.delete(num);
            if(result != null)return result;
        }

        //�ݹ����ӽڵ�ɾ������
        if(this.right != null){
            result = this.right.delete(num);
            if(result != null)return result;
        }
        return result;
}

//BinaryTreeɾ������
public PersonNode delete (int num){
        PersonNode res = null;
        if(this.root != null){
            if(this.root.getNum() == num){
                res = this.root;
                this.root = null;
            }else{
                res = this.root.delete(num);
            }
        }
        if(res == null){
            System.out.println("binary tree is empty.");
        }else{
            System.out.println("ɾ���ڵ㣺" + res);
        }
        return res;
}
```



˼����������ĳɣ�����ҵ��ýڵ㣬ɾ���ýڵ㣬������ӽڵ㲻Ϊ�գ��ͽ����ӽڵ�Ź��������Ϊ�գ����ж����ӽڵ��Ƿ�Ϊ�գ���Ϊ�վͷ����ӽڵ�



##### 4��˳��洢������

����˵���������ݴ洢����������洢��ʽ�����Ĵ洢��ʽ�����໥ת����Ҳ����������ת��Ϊ���飬�������ת��Ϊ����



˳��洢�������ĵ��ص㣺

��1��˳�������ͨ��ֻ������ȫ������

��2����n��Ԫ�ص����ӽڵ�ŵ�2\*n + 1��Ԫ�أ����ӽڵ��ŵ�2\*n + 2��Ԫ��

��3����n��Ԫ�صĸ��ڵ�Ϊ(n - 1) / 2

��4��n��ʾ�������ĵ�n��Ԫ��

��5��ֻ�ǹ涨���˳�򣬺ͽڵ���������ŵ�ֵû�й�ϵ



˳��洢������

![](�㷨img/˳��洢������.png)



˳��洢����������ʵ��

```java
public class ArrayBinaryTree {
    public static void main (String[] args){
        int[] arr = {1,2,3,4,5,6,7};
    }
    
    private int[] arr;
    public ArrayBinaryTree (int[] arr){
        this.arr = arr;
    }
    
    public void preOrder () {
        this.preOrder(0);
    }
    
    //ǰ�������index=0
    public void preOrder (int index){
        if(arr = null || arr.length = 0){
            System.out.println("Array should not be null.");
            return;
        }
        System.out.println(arr[index]);
        if(index * 2 + 1 < arr.length){
            preOrder(2 * index + 1);
        }
        if(index * 2 + 2 < arr.length){
            preOrder(2*index + 2);
        }
    }
    
     //�������
    public void infixOrderList (int index){
        //����û�г�ʼ�����򴫵ݿ����鴦��
        if(arr == null || arr.length == 0){
            System.out.println("Array should not be null.");
            return;
        }
        if(index*2 + 1 < arr.length){
            infixOrderList(index*2 + 1);
        }
        System.out.print(arr[index] + "\t");
        if(index*2 + 2 < arr.length){
            infixOrderList(index*2 + 2);
        }
    }

    //�������
    public void postOrderList (int index){
        //����û�г�ʼ�����򴫵ݿ����鴦��
        if(arr == null || arr.length == 0){
            System.out.println("Array should not be null.");
            return;
        }
        if(index*2 + 1 < arr.length){
            postOrderList(index*2 + 1);
        }
        if(index*2 + 2 < arr.length){
            postOrderList(index*2 + 2);
        }
        System.out.print(arr[index] + "\t");
    }
}
```



ʹ�ó��������������õ����ݽṹ����˳��洢������



##### 5��������������

������{1��3��6��8��10��14}������һ�ö�����

��������

```java
		1
 	3		6
  8	  10  14         
```

���⣺�Զ��������б���ʱ��6��8��10��14�⼸���ڵ������ָ�룬��û����ȫ�������ϣ���������������ø����ڵ������ָ�룬�ø����ڵ�ָ���Լ���ǰ��ڵ���ô�죿



���������������������



��������������Threaded Binary Tree��

��1��n���ڵ�Ķ��������к���n+1����ָ����2n-��n-1��= n+1����

***�Ƶ���***n��Ԫ�ػ����2n��ָ�룬������������������Ҫn-1��ָ�����ӣ����Կ�ָ������`2n-(n-1)`��

��2�����ö�������Ŀ�ָ���򣬴��ָ��ýڵ���ĳ�ֱ��������µ�ǰ���ͺ�̽ڵ��ָ�룬���ָ��ӵ�ָ���Ϊ**����**��

��ͬ�ı�����ʽ��ָ��ָ��Ľڵ㲻ͬ

��3�����������Ķ��������Ϊ**��������**����Ӧ�Ķ�������Ϊ**����������**��

��4�������������ʵĲ�ͬ��������������Ϊ**ǰ������������**��**��������������**��**��������������**��

��5��һ���ڵ��ǰһ����㣬��Ϊ**ǰ���ڵ�**��һ���ڵ�ĺ�һ���ڵ��Ϊ**��̽ڵ�**



Ӧ�ð���������������--{8��3��10��1��14��6}

```java
	    1 
   3          6 
 8  10      14
//������������������
//8����ָ��ָ��3��10����ָ��ָ��3����ָ��1
//14����ָ��ָ��1����ָ��ָ��6
```

˵�������������������󣬽ڵ������left��right�������������

��1��left��ָ������������Ҳ������ָ��ǰ���ڵ㣬����1�ڵ����������������ָ��ָ��10��ʵ��ָ��3����ָ��ָ��14��ʵ��ָ��6��10�ڵ���ָ��ָ����ǰ���ڵ㣻

��2��rightָ�������������Ҳ������ָ���̽ڵ㣬����1�ڵ��rightָ���������������10�ڵ�õ�rightָ����Ǻ�̽ڵ㡣



��������������ʵ�֣�

<font color="red">ע�������Ҷ�ӽڵ���ָ�룬�����ҵ�Ҷ�ӽڵ����ָ�붼�ǲ��ᱻ������������</font>

```java
public class ThreadedBinaryTree {
    private HeroNode root;
    
    //�ݹ������������ʱ�����Ǳ���ǰ���ڵ�
    private HeroNode prev = null;
    
    //��������������������ķ���
    public void threadedNodes (PersonNode node) {
        if(node == null){
            return;
        }
        //1.��������������
        threaded(node.getLeft());
        
        //2.��������ǰ�ڵ�
        //2.1�ȴ���ǰ�ڵ��ǰ���ڵ�
        if(node.getLeft() == null){
            node.setLeft(prev);
            node.setLeftType(false);
        }
        
        //2.2�����̽ڵ�
        if(prev!= null && prev.getRight() == null){
            //��ǰ���ڵ����ָ��ָ��ǰ�ڵ�
            prev.setRight(node);
            prev.setRight(false);
        }
        //ÿ����һ���ڵ㣬�õ�ǰ�ڵ�����һ���ڵ��ǰ���ڵ�
        prev = node;
        
        //3.������������
        threaded(node.getRight());
    }
}
//��PersonNode�й涨��
//leftType:true��������falseǰ���ڵ�
//leftType:true��������false��̽ڵ�
```



����������������

�����ڵ����ͨ�����Է�ʽ�������������ݹ飬����˱���Ч�ʣ���������Ӧ�����������һ��

```java
//�������
public void threadedList () {
    PersonNode temp = root;
    while(temp != null){
        while(temp.getLeftType()){
            temp = temp.getLeft();
        }
        //������ڵ㲢���
        System.out.println(temp);
        //һֱ�����̽ڵ�
        while(!temp.getRightType()){
            temp = temp.getRight();
            System.out.println(temp);
        }
        node = node.getRight();
    }
}
```



#### 4�����ݽṹ���㷨��Ӧ��

##### 1�������������ʵ��

��1�������������ö��������ݽṹ����������һ��ѡ���������������á�ƽ��ʱ�临�Ӷȶ���O(nlog n)���ǲ��ȶ�����

��2��������ȫ������

+ ÿ���ڵ��ֵ�������ڵ������Һ��ӽڵ��ֵ����Ϊ**�󶥶�**
+ û��Ҫ�����Һ��ӽڵ��ֵ
+ ÿ���ڵ��ֵ��С�ڻ�������Һ��ӽڵ��ֵ����Ϊ**С����**

��3��������ô󶥶ѣ��������С����



������˼��

��1�������������нṹ����һ���󶥶ѣ�����Ҫ������������

��2����ʱ�������е����ֵ���ǶѶ��ĸ��ڵ�

��3��������ĩβԪ�ؽ��н�������ʱĩβ�������ֵ

��4��Ȼ��ʣ��n-1��Ԫ�����¹���һ���ѣ�������õ�n��Ԫ�صĴ�Сֵ����˷���ִ�У����ܵõ�һ�����������ˡ�

���Կ��������󶥶ѵĹ����У�Ԫ�صĸ����𽥼��٣����õ�һ���������С�



���������˼·

��1�����������й���Ϊһ���ѣ��󶥶ѻ�С���ѣ�

��2�����Ѷ�Ԫ�غ�ĩβԪ�ؽ���������Ԫ�س�������ĩ��

��3�����µ����ṹ��ʹ�����㶨�壬Ȼ����������Ѷ�Ԫ���뵱ǰĩβԪ�أ�����ִ�е�����������֪��������������



���������ʵ��

```java
public class HeapSort{
    public void heapSort (int[] arr){
       //���ݷ�Ҷ�ӽڵ����¶���������ֵ���ϸ�
        for(int i = arr.length/2 - 1; i >= 0; i--){
            adjustHeap(arr,i,arr.length);
        }
        //���ϸ���ֵ�������������
        int temp = 0;
        for(int j = arr.length-1;j>0;j--){
            temp = arr[j];
            arr[j] = arr[0];
            arr[0] = temp;
            adjustHeap(arr,0,j);
        }
    }
    
    //ע���Ҷ�ӽڵ�i�����¶��ϵ�
    //����Ϊ���������飬i��ʾ��Ҷ�ӽڵ�����������
    //length�Ѷ��ٸ�Ԫ�ؽ��е�����length���𽥼���
    //���ܣ���ɽ���Ҷ�ӽڵ���������ɴ󶥶�
    public void addjustHeap (int[] arr,int i,int length){
        int temp = arr[i];
        for(int k = i*2 + 1; k < length; k = k*2 +1){
            //������ӽڵ�����ӽڵ�С���е����ӽڵ�
            if(k + 1 < length && arr[k] < arr[k+1]){
                k++;//ָ�����ӽڵ�
            }
            //�ҵ��ӽڵ��бȽϴ���뵱ǰ��Ҷ�ӽڵ�Ƚ�
            if(arr[k] > temp){
                //����ӽڵ���ڸ��ڵ㣬�ѽϴ��ֵ��ֵ����ǰ�ڵ㣬��iָ��k
                arr[i] = arr[k];
                //�л�����ǰ�ڵ����һ���ڵ����ѭ���Ƚ�
                i = k;
            }else{
                break;//
            }
        }
        //��ѭ���������Ѿ���iΪ���ڵ���������ֵ�����������
        //���ҵ��ķ�Ҷ�ӽڵ�ֵ��ֵ��ȥ����ɽ���
        arr[i] = temp;
    }
}
```



�������ٶ��ر�죬���ǵݹ���ǵ���������ǿ



##### 2���շ�����

��������

��1������n��Ȩֵ��Ϊn��Ҷ�ӽڵ㣬����һ�ö���������������Ĵ�Ȩ·�����ȴﵽ��С������������Ϊ���Ŷ�����

��2��**�շ������Ǵ�Ȩ·��������̵���**��Ȩֵ�ϴ�Ľڵ�����Ͻ�,

?		WPL��С����



�շ�������Ҫ����

��1����һ��������һ���ڵ����´ﵽ���ӻ����ӽڵ�֮���ͨ·����Ϊ**·��**��ͨ·�з�֧����Ŀ��Ϊ**·������**�����涨����ΪL����L���·������ΪL-1.

��2���������нڵ㸳��һ������ĳ�ֺ������ֵ���������ֵ��Ϊ�ýڵ��**Ȩ**��

��3��**�ڵ�Ĵ�Ȩ·������**���Ӹ��ڵ㵽�ýڵ�֮���·��������ýڵ��Ȩ�ĳ˻�����·��������2��Ŀ��ڵ�ȨֵΪ5����Ȩ·������Ϊ10��

��4��**���Ĵ�Ȩ·������**�����Ĵ�Ȩ·�����ȹ涨Ϊ����Ҷ�ӽڵ�Ĵ�Ȩ·��֮�ͣ���ΪWPL��weighted path length��

��5��WPL��С�ľ���**�շ�����**



�շ���������˼·��

��1���Ƚ������С�����������ÿһ�����ݶ���һ���ڵ㣬ÿ���ڵ���Կ�����һ����򵥵Ķ�����

��2��ȡ���ڵ�Ȩֵ��С�����ö�����

��3�����һ���µĶ����������µĶ������ĸ��ڵ��Ȩֵ��ǰ�����ö��������ڵ�Ȩֵ�ĺ�

��4��������µĶ��������Ը��ڵ��Ȩֵ��С�ٴ����򣬲����ظ���ֱ�������У��������ݶ��������͵õ�һ�úշ�����



javaʵ�ֺշ�����

```java
public class HuffmanTree {
    public static void main(String[] args){
        int[] arr = {13,7,8,3,29,6,1};
        createHuffmanTree(arr);
    }
    
    //�������飬�������ÿһ��Ԫ�ع�����һ��Node���뵽ArrayList��
    public static void createHuffmanTree (int[] arr){
        List<Node> nodes = new ArrayList<>();
        for(int value : arr){
            nodes.add(new Node(value));
        }
        
        while(nodes.size > 1){
            //��С��������,java�Դ�������
        	Collections.sort(nodes);
        	Node leftNode = nodes.get(0);
            Node rightNode = nodes.get(1);
      Node parentNode = new Node(leftNode.value+rightNode.value);
            parentNode.left = leftNode;
            parentNode.right = rightNode;
            nodes.remove(leftNode);
            nodes.remove(rightNode);
            nodes.add(parentNode);
            Collections.sort(nodes);
        }
    }
    
    //ǰ�����
    public static void preOrder(Node root){
        if(this.root != null){
            this.root.preOrder();
        }else{
            System.out.println("root is null.");
        }
    }
}
//Ϊ����Node�ܳ�������ʵ��Comparable�ӿ�
class Node implements Comparable<Node> {
    int value;
    Node left;
    Node right;
    
    public void preOrder () {
        System.out.println(this);
        if(this.left != null){
            this.left.preOrder();
        }
        if(this.right != null){
            this.right != null;
        }
    }
    
    public Node (int value){
        this.value = value;
    }
    
    public int compareTo (Node target){
        //��С��������
        return this.value - target.value;
    }
}
```



##### 3���շ�������

��������

��1���շ���������һ�ֱ��뷽ʽ������һ�ֳ����㷨

��2���շ��������Ǻշ�������ͨ�ŵ���ľ���Ӧ��֮һ

��3���շ�������㷺���������ļ�ѹ����ѹ����ͨ����20%-90%֮��

��4���շ��������ǿɱ䳤���룬Huffman��1952������ı��뷽������֮Ϊ��ѱ���



ԭ�����

ͨ�������е���Ϣ����ʽ---��������

> �ַ�����`i like java i like java a`
> ASCII�룺 `105(i),32(�ո�),108(l),105,107,101,32,106,97,118,97...`
>
> 1.����������ǽ���Щ�ַ��Ķ����ƶ����棬Ȼ����д���
>
> �����ƣ�`01101001(i),etc...`�������Ƚϴ�
>
> 2.�ɱ䳤����
> ��1��ͳ�ƴ���
> 	`i:4 l,k,e,v,j:2 a:5 �ո�:6`
> ԭ���ϣ����ո����ַ����ֵĴ������б��룬���ִ���Խ��ģ�����ԽС
> ��2�������Ʊ�ʾ�ַ�
>
> `�ո�:0 a:1 i:10 e:11 j:100 k:101 l:110 v:111 `
> ��3�������������ɱ䳤����Ϊ
> `10(i) 0(�ո�) 110(l) 10(i) 101(k) 11(e) 0 100 1 111 1...`
>
> ǰ׺���룺�ַ��ı��벻���������ַ������ǰ׺��������ƥ�䵽�ظ��ı���
>
> �������⣺����ǰ׺���룬���״��ڶ����ԣ�����`i(10)`��`k(101)`��ǰ׺



�շ�������

ͨ������ĵ����ֱ��뷽ʽ

> 1���ַ���`i like java i like java a`
>
> 2��ͳ���ַ����ִ���`i:4 l,k,e,v,j:2 a:5 �ո�:6`
>
> 3�����������ַ����ֵĴ�������һ�úշ����������ִ�����ΪȨ
>
> 4�������ݰ��չ��򹹽���һ�úշ�����
>
> 5�����ݺշ�����������Ϊ0������Ϊ1���ҵ��ڵ��·�����Ǹ����ĺշ�������
>
> �����ı������ǰ׺���룬��ÿһ���ַ��ı��붼��������һ���ַ������ǰ׺ԭ����Ϊ����Ҷ�ӽڵ��ʾһ���ַ����������е�Ҷ�ӽڵ��·����Ψһ��
>
> 6�����õ��ı�����ǻ��������루����ѹ����
>
> 7��**ע�⣺**�շ������ظ����ݳ��ֵ�ʱ�����п��ܳ��ֲ�ͬ�ĺշ����������Ա���Ҳ����ֲ�ͬ�ı�����������ѹ����ĳ�����һ���ģ���������ѹ��



�շ�������---����ѹ��

˼·������

��1��Node�ڵ㣬�������ݡ�Ȩ�ء���ڵ㡢�ҽڵ�

��2�����õ����ַ����ŵ���Ӧ��byte[]���飬��׼�������շ�������Node�ڵ�ŵ�List

��3��ͨ��List������Ӧ�ĺշ�����



�����շ���������

```java
public class HuffmanCode {
    public static void main (String[] args){
        String str = "I like java do you like java really";
        byte[] bytes = str.getBytes();
    }
    
    public static List<Node> getNodeList (byte[] bytes) {
        //��һ��List������нڵ�
        ArrayList<Node> nodes = new ArrayList<>();
        //��һ��Map����ͳ���ֽڳ��ֵĴ���
        Map<Byte,Integer> counts = new HashMap<>();
        for(byte b : bytes){
            Integer count = counts.get(b);
            if(count == null){
                counts.put(b,1);
            }else{
                //����
                counts.put(b,count++);
            }
        }
        //����Map���ڵ�ŵ�List������
        for(Map.entry<Byte,Integer> entry : counts.entrySet()){
            nodes.add(new Node(entry.getKey(),entry.getValue()));
        }
        return nodes;
    }
    
    //�����շ����������ظ��ڵ�
    public static Node createHuffmanTree (byte[] bytes) {
        List<Node> nodes = getNodeList(bytes);
        while(nodes.size() > 1){
            Collections.sort(nodes);
            Node leftNode = nodes.get(0);
            Node rightNode = nodes.get(1);
            Node parent = new Node(null,leftNode.getWeight()+rightNode.getWeight());
            parent.setLeft(leftNode);
            parent.setRight(rightNode);
            nodes.remove(leftNode);
            nodes.remove(rightNode);
            nodes.add(parent);
        }
        return nodes.get(0);
    }
}

class Node {
    //�������
    private Byte data;
    //��ʾ�ַ����ִ���
    private int weight;
    private Node left;
    private Node right;
    
    public Node (Byte data,int weight){
        this.data = data;
        this.weight = weight;
    }
    
    public int compareTo (Node o){
        return this.weight - o.weight;
    }
    
    public void toString (){
        return "Node[data=" + data + ",weight=" + weight + "]"; 
    }
    
    public void preOrder () {
        System.out.println(this);
        if(this.getLeft() != null){
            this.getLeft().preOrder();
        }
        if(this.getRight() != null){
            this.getRight().preOrder();
        }
    }
}
```



��úշ�������

�γ̴���

```java
private static HashMap<Byte,String> byteToCodeMap = new HashMap<>();
public static void getCodes (Node node,String code,StringBuilder sb) {
    StringBuilder sb2 = new StringBuilder(sb);
    sb2.append(code);
    if(node != null){
       if(node.getData() == null){
           getCodes(node.getLeft(),"0",sb2);
           getCodes(node.getRight(),"1",sb2);
       }else{
           byteToCodeMap.put(node.getData(),sb2.toString());
       }
    }
}
```

�Լ����룺

```java
//�涨�����·��Ϊ0�����ҵ�·��Ϊ1
    public static void getHuffmanCode (Node node,Map<Byte,String> byteToCodeMap,StringBuilder str) {
        if(node.getLeft() == null && node.getRight() == null){
            byteToCodeMap.put(node.getData(),str.toString());
            return;
        }
       if(node.getLeft() != null){
           str.append("0");
           getHuffmanCode(node.getLeft(),byteToCodeMap,str);
           //�ݹ�ظ����ڵ�ɾ����֧��ӵ��ַ�
           str = str.deleteCharAt(str.length()-1);
       }
       if(node.getRight() != null){
           str.append("1");
           getHuffmanCode(node.getRight(),byteToCodeMap,str);
           //�ݹ�ظ����ڵ�ɾ����֧��ӵ��ַ�
           str = str.deleteCharAt(str.length()-1);
        }
    }
```



��ȡ�շ����������ֽ�����

```java
//bytes ԭʼ�ַ�����Ӧ���ֽ�����  
//Map �շ�������Map
//����ֵ�������շ����ֽ�����
//ע�����ɵĺշ��������ǲ��룬-1��÷��룬����λ���䣬��λȡ�����ԭ��
private static byte[] zip(byte[] bytes,Map<Byte,String huffmanCodeMap){
    StringBuilder sb = new StringBuilder("");
    for(byte b : bytes){
        sb.append(huffmanCodeMap.get(b));
    }
    //����Ӧ�ַ���תΪbyte����
    //ͳ�Ʒ��غշ������볤��
    //��Ϊÿ���ֽڶ���8λ�����Բ���Ҫ��0
    int len = (sb.length() + 7) / 8;
    //�ȼ���len = sb.length() % 8 == 0 ? sb.length % 8 : sb.length() % 8 + 1;
    //�����洢ѹ�����byte���飬��СΪlen
    byte[] newByteArr = new byte[len];
    int index = 0;
    for(int i = 0; i < sb.length(); i+=8){
        String temp = "";
        //��ֹԽ�磬���һλ����ǿת��ʱ��0
        if(i + 8 > sb.length()){
            temp = sb.substring(i);
        }else{
            temp = sb.substring(i,i + 8);
        }
        newByteArr[index++] = (byte)Integer.parseInt(temp,2);
    }
    return newByteArr;
}
```



�շ����ֽ��������

```java
//������ݽ�ѹ
//1.���ֽ�ת���ɶ�����
//2.�������Ӧ�Ķ������ַ������պշ���Mapת��Ϊ�ַ���
//3.flag��ʶ����
//4.����ֵ���ֽڶ�Ӧ�Ķ������ַ���
public static String byteToBitString (byte b,boolean flag) {
     int temp = b;//��bת��int����
        
     //������������ڲ���λ
     if(flag){
        //����1��ȡ�������ַ�����1
        // 256|1: 1 0000 0000 | 0000 0001 100000001
        temp |= 256;
     }
        
     //��ȡ�ֽڶ�Ӧ�Ĳ��뵫��������ȥ������0��
      //4: 100,������Ҫ����Ĳ�����0
      String str = Integer.toBinaryString(temp);
      if(flag){
         //����Ϊ9����Ҫ�ѵ�һ���ɵ�
         return str.substring(str.length()-8);
      }else{
         //���һ���ֽ��ǲ���Ҫ����λ��
         //���غ����ͨ��Integer�ķ���תInt����
         return str;
      }
}
    
//��ɶ�ѹ�����ݵĽ���
public static byte[] decode (Map<Byte,String> huffmanCodeMap,byte[] huffmanBytes){
    StringBuilder sb = new StringBuilder("");
    //��byte����ת�ɶ������ַ���
    for(int i = 0; i < huffmanBytes.length;i++){
        boolean flag = (i!=huffmanBytes.length-1);
        sb.append(byteToBitString(huffmanBytes[i],flag));
    }
    //��ԭ����Map��ת������ͨ���ַ�����ȡ�ֽ�
    Map<String,Byte> reverseMap = new HashMap<String,byte>;
    for(Map.Entry<Byte,String> entry : byteToCodeMap){
        reverseMap.put(entry.getValue(),entry.getKey());
    }
    //���������ַ�����Ӧ���ֽ�ȡ���ŵ�������
    List<Byte> list = new ArrayList<>();
    for(int i = 0; i < sb.length();){
        int count = 1;
        boolean flag = true;
        Byte b = null;
        while(flag){
            String key = sb.substring(i,i+count);
            b = map.get(key);
            if(b == null){
                count++;
            }else{
                flag = false;
            }
        }
        list.add(b);
        i += count;
    }
}
```



ͨ�����������뷽�����ļ�����ѹ��

```java
//srcFile��Դ�ļ�·��  outFile������ļ�·��
public static void zipFile (String srcFile,String outFile){
    FileInputStream fis = null;
    FileOutputStream fos = null;
    ObjectOutputStream oos = null;
    try{
        fis = new FileInputStream(srcFile);
        byte[] b = new byte[fis.available];
        fis.read(b);
        //��ȡѹ���������
        byte[] zipBytes = zip(b);
        fos = new FileOutputStream(outFile);
        //���������������Ϊ���Ժ�ظ�Դ�ļ�ʹ��
        oos = new ObjectOutputStream(fos);
        oos.writeObject(zipBytes);
        //��byte��String��ӳ���ϵд���ļ�
        oos.writeObject(byteToCodeMap);
        oos.flush();
    }catch(Exception e){
        e.printStackTrace();
    }finally{
        try{
            fis.close();
            fos.close();
            oos.close();
        }catch(Exception e){
            e.printStackTrace();
        }
    }
}
```



�շ���ѹ���ļ���ѹ

```java
public static void unZipFile (String src,String out) {
    //�����ļ���������
    FileInputStream fis = null;
    ObjectInputStream ois = null;
    FileOutputStream fos = null;
    try{
        fis = new FileInputStream(src);
        ois = new ObjectInputStream(fis);
        byte[] huffmanBytes = (byte[])ois.readObject();
        Map<Byte,String> map = (Map<Byte,String>)ois.readObject();
        decode();
    }catch(Exception e){
        e.printStackTrace();
    }
}
```



�շ���ѹ���ļ�ע������

��1������ļ�������Ǿ���ѹ������ģ���ʹ�úշ�������ѹ��ѹ��Ч�ʲ��������Ա仯��������Ƶ��ppt���ļ���������Ǿ���ѹ�����ļ�

��2���շ��������ǰ����ֽڴ���ģ����Կ�������ѹ�����е��ļ�

��3�����һ���ļ����ظ������ݲ��࣬ѹ��Ч��Ҳ������



#### 5������������

�������������ܣ�BST��Binary sort tree�������ڶ��������κ�һ����Ҷ�ӽڵ㣬Ҫ�����ӽڵ��ֵ�ȵ�ǰ�ڵ�ֵС�����ӽڵ��ֵ�ȵ�ǰ�ڵ��ֵ��



������������Ӻͱ�����������

```java
public class BinarySortTree {
    Node root;
    
    public BinarySortTree (){}
    
    public void add(Node node){
        if(root == null){
            root = node;
        }else{
            root.add(node);
        }
    }
    
    public void infixOrder () {
        if(root != null){
            root.infixOrder();
        }else{
            System.out.println("tree is null.");
        }
    }
}

class Node {
    int value;
    Node left;
    Node right;
    
    public Node (int value){
        this.value = value;
    }
    
    //��ӽڵ�
    public void add(Node node){
        if(node == null){
            return;
        }
        //��ӽڵ�ֵ�뵱ǰ�ڵ�ֵ���д�С�Ƚ�
        if(node.value < this.value){
            if(this.left == null){
                this.left = node;
            }else{
                this.left.add(node);
            }
        }else{
            if(this.right == null){
                this.right = node;
            }else{
                this.right.add(node);
            }
        }
    }
    
    //���������������������������������
    public void infixOrder () {
        if(this.left != null){
            this.left.infixOrder();
        }
        System.out.println(this);
        if(this.right != null){
            this.right.infixOrder();
        }
    }
}
```



ɾ��������

��1��ɾ��Ҷ�ӽڵ�

+ û�и��ڵ����

+ �ҵ�Ҫɾ���Ľڵ�͸��ڵ㣬�����������У�����ָ����ÿ�

��2��ɾ��ֻ��һ�������Ľڵ�

+ �ҵ�Ҫɾ���Ľڵ�͸��ڵ�
+ ȷ�������ӽڵ㻹�����ӽڵ�
+ ���ɾ�����Ǹ��ڵ�����ӽڵ�

��3��ɾ�������������Ľڵ�

��������������Ҷ�ӽڵ㣬ɾ����ǰ�ڵ㣬Ȼ������



����������ɾ���ڵ㷽��

```java
class Node {
    int value;
    Node left;
    Node right;
    
    //����Ҫɾ���ڵ��ֵ
    public Node search (int value){
        if(value == this.value)return this;
        if(value < this.value){
            //����߼�������
            if(this.left == null)return null;
            return this.left.search(value);
        }else{
            //���ұ߼�������
            if(this.right == null)return null;
            return this.right.search(value);
        }
    }
    
    //����Ҫɾ���ڵ�ĸ��ڵ��ֵ
    public Node searchParent (int value){
        if((this.left != null && this.left.value == value) || (this.right != null && this.right.value == value)){
            return this;
        }else{
            //������ҵ�ֵС�ڵ�ǰ�ڵ��ֵ�����ҵ�ǰ�ڵ�����ӽڵ㲻Ϊ��
            if(value < this.left.value && this.left != null){
                return this.left.searchParent(value);
            }else if(this.right != null){
                //ע��ʵ�������Ҫ������ֵͬ�����
                return this.right.searchParent(value);
            }else{
                //�������㣬�������Ǹ��ڵ㣬���ڵ�û�и��ڵ�
                return null;
            }
        }
    }
}

class BinarySortTree {
    private Node root;
    
    //����Ҫɾ���ڵ�
    public Node search (int value){
        if(root == null){
            return null;
        }else{
            return root.search(value);
        }
    } 
    
    //���Ҹ��ڵ�
    public Node searchParent (int value){
        if(root == null){
            return null;
        }else{
            return root.searchParent(value);
        }
    }
    
    //�ҵ��ڵ������Ҷ�ӽڵ㲢ɾ������ڵ�
    public int deleteRightTreeMini (Node node){
        Node target = node;
        while(target.left != null){
            target = target.left;
        }
        deleteNode(target.value);
        return target.value;
    }
    
    //ɾ���ڵ�
    public void deleteNode (int value){
        if(root == null){
            return;
        }else{
            Node target = search(value);
            //û�ҵ�Ҫɾ���ڵ�
            if(target == null)return;
            
            //����ҵ�����root�ڵ㣬������������С�ڵ�ɾ��
            //���ڵ��ж�
            if(target == root){
                if(target.right != null){
                    int val = deleteRightTreeMini(target.right);
                    root.value = val;
                    return;
                }else if(target.left != null){
                    root = target.left;
                    return;
                }else{
                    root = null;
                    return;
                }
            }
            
            //target�ҵ����Ҹ��ڵ�
            Node parent = searchParent(value);
            
            //2��target��Ҷ�ӽڵ�
            if(target.left == null && target.right == null){
                //�ж�����Ҷ�ӽڵ㻹����Ҷ�ӽڵ�
                if(parent.left != null && target.left.value == value){
                    parent.left = null;
                }else if(parent.right != null && parent.right.value == value){
                   parent.right = null; 
                }
            }else if(target.left != null && target.right != null){
                //3��ɾ�������������Ľڵ㣬�ҵ���������С�ڵ㣬�����������ڵ�
                int minVal = deleteRightTreeMini(target.right);
                targetNode.value = minVal;
            }else{
                //4��targetֻ��һ���������
                if(target.left != null){
                    //4.1 target��������
                    //�ж�target��parent�����ӽڵ㻹�����ӽڵ��������
                    if(parent.left.value == value){
                        parent.left = target.left;
                    }else{
                        parent.right = target.left;
                    }
                }else{
                    //4.2 target��������
                    //�ж�target��parent�����ӽڵ㻹�����ӽڵ��������
                    if(parent.left.value == value){
                        parent.left = target.right;
                    }else{
                        parent.right = target.right;
                    }
                }
            }
        }
    }
}
```



�Լ����Դ��루�޸Ŀγ����жϲ��Ͻ��ĵط���

```java
public class BinarySortTree {
    private static Node root;

    public static void add (Node node) {
        if(root == null){
            root = node;
        }else{
            root.add(node);
        }
    }

    //Ѱ�ҽڵ�
    public static Node findNode (int value){
        if(root == null){
            return null;
        }else{
            return root.findNode(value);
        }
    }

    //Ѱ�ҽڵ�ĸ��ڵ�
    public static Node findParent (int value) {
        if(root == null)return null;
        return root.findParent(value);
    }

    //�������
    public static void infixOrder (){
        if(root == null){
            System.out.println("tree is empty.");
        }else{
            root.infixOrder();
        }
    }

    //ɾ������������Ľڵ�
    public static Node delRightTreeMin (Node node){
        Node temp = node;
        Node parent = node;
        while(temp.getLeft() != null){
            temp = temp.getLeft();
        }
        delete(temp.getValue());
        return temp;
    }

    //ɾ���ڵ�
    /*
     * 1��ɾ��Ҷ�ӽڵ�
     * 2��ɾ���ڵ�ֻ��һ������
     * 3��ɾ���ڵ�����������
     * 3.1�������������ҽڵ�
     * 3.2��������������ڵ㶥��
     * 4��ɾ���ڵ��Ǹ��׽ڵ�
     * */
    public static void delete (int value){
        if(root == null)return;
        //�ҵ�Ҫɾ���ڵ�
        Node target = findNode(value);
        if(target == null)return;

        //ɾ�����ڵ㴦��
        if(target == root){
            //����������Сֵ�滻
            if(target.getRight() != null){
                root.setValue(delRightTreeMin(target.getRight()).getValue());
            }else if(target.getLeft() != null){
                root = root.getLeft();
            }else{
                root = null;
            }
            return;
        }

        //ɾ�����ڵ�����ڵ�
        Node parent = findParent(value);
        //ɾ��Ҷ�ӽڵ�
        if(target.getLeft() == null && target.getRight() == null){
            if(parent.getLeft() != null && parent.getLeft().getValue() == value){
                parent.setLeft(null);
            }else if(parent.getRight() != null && parent.getRight().getValue() == value){
                parent.setRight(null);
            }
        }else if(target.getLeft() != null && target.getRight() != null){
            //ɾ�������������ڵ�
            int rightMiniVal =  delRightTreeMin(target.getRight()).getValue();
            target.setValue(rightMiniVal);
        }else{
            //ɾ��ֻ��һ�������Ľڵ�
            if(target.getLeft() != null){
                //���������ҵ�parent��
                if(parent.getLeft() != null && parent.getLeft().getValue() == value){
                    parent.setLeft(target.getLeft());
                }else{
                    parent.setRight(target.getLeft());
                }
            }else{
                //���������ҵ�parent��
                if(parent.getLeft().getValue() == value){
                    parent.setLeft(target.getRight());
                }else{
                    parent.setRight(target.getRight());
                }
            }
        }
    }
}

class Node {
    private int value;
    private Node left;
    private Node right;

   //getter,setter...

    public Node (int value){
        this.value = value;
    }

    //���ӽڵ�ķ���
    public void add (Node node) {
        if(node == null)return;
        if(node.getValue() < this.getValue()){
            if(this.getLeft() != null){
                this.getLeft().add(node);
            }else{
                this.setLeft(node);
            }
        }else{
            if(this.getRight() != null){
                this.getRight().add(node);
            }else{
                this.setRight(node);
            }
        }
    }

    public Node findNode (int value) {
        //�����ǰ�ڵ�ֵ���ڲ���ֵ������
        if(value == this.getValue())return this;
        //����ȵ�ǰ�ڵ�ֵС���ȴ���߲��ң�������ӽڵ�Ϊ��
        //����ȵ�ǰ�ڵ�ֵ�󣬴��ұ߲��ң�������ӽڵ�Ϊ��
        if(value < this.getValue()){
            if(this.getLeft() == null)return null;
            return this.getLeft().findNode(value);
        }else{
            if(this.getRight() == null)return null;
            return this.getRight().findNode(value);
        }
    }

    public Node findParent (int value){
        //�ҵ�����ֹ�ݹ����������ӽڵ�����ӽڵ�ֵ���ڲ��ҽڵ�ֵ
        if(( this.getLeft() != null && this.getLeft().getValue() == value ) || (this.getRight() != null && this.getRight().getValue() == value)){
            return this;
        }else{
            //value�͵�ǰ�ڵ�ֵ�ıȽϽ�����һ����֧�ıȽ�
            if(this.getLeft() != null && this.getValue() > value){
               return this.getLeft().findParent(value);
            }else if(this.getRight() != null && this.getValue() <= value){
                return this.getRight().findParent(value);
            }else{
                return null;
            }
        }
    }

    //�������
    public void infixOrder (){
        if(this.getLeft() != null){
            this.getLeft().infixOrder();
        }
        System.out.println(this);
        if(this.getRight() != null){
            this.getRight().infixOrder();
        }
    }

    @Override
    public String toString() {
        return "Node{" +
                "value=" + value +
                '}';
    }
}
```



#### 6������ƽ����