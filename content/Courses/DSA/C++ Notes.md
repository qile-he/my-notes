```cpp
(int)c        // 字符 → ASCII码
c - '0'       // 数字字符 → 数字
x + '0'       // 数字 → 数字字符
```

可以利用`insert`把一个`str`插入到另一个`str`类型去
```cpp
string a = "hello";
string b = "123";
a.insert(2, b);//a="he123llo
s.insert(pos, str);
```
第三句代表把 `b` 插入到 `a` 的下标 `2` 的位置
	如果想直接拼接到末尾，直接相加或`append`即可

```cpp
string t = s.substr(start, len);
s.substr(2);//只写一个参数代表一直到结尾

string left = s.substr(0, 3);
string right = s.substr(3);//将字符串分为两个部分
```

```cpp
string s = "abcdefg";
int index;
int pos = s.find("cde", index);//find用来查找，从第index位开始查找， 
if (pos != string::npos) {
    // 找到了
}
```

```cpp
s.erase(start, len);
s.erase(s.begin() + 2);//代表删除下表为2的字符
```

```cpp
string s = "abcdefg";
s.replace(2, 3, "XYZ");//从下标2开始，删除3个字符，然后换成"XYZ"
```

```cpp
vector<int> a = {10, 20, 30, 40};
auto it = find(a.begin(), a.end(), 30);
cout << it - a.begin();   // 2

find(v.begin(), v.end(), x) != v.end()
```

把`int`转换为`string`
```cpp
to_string(1);
string newstr = str + to_string(j);
```

```cpp
tolower(s)//把大写字母转化为小写字母，数字则不变，不会修改原变量 写法：s=tolower(s)
toupper(s)
islower(s)
isupper(s)
isdigit(s)
isalpha(s)
```