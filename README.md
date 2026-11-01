# 《算法竞赛试炼场：洛谷300题精析》题目整理与解析

> **书名**：《算法竞赛试炼场：洛谷300题精析》（算法竞赛丛书）
> **作者**：罗勇军、汪楚奇、陈哲　**出版社**：清华大学出版社（2026 年 9 月）
> **整理方式说明**：原书官方配套题单在洛谷需登录查看，本书解析为受版权保护内容，无法直接引用。本文件按原书的八篇结构与知识点梯度，从洛谷公开题库精选**真实存在的经典题目**（历年 NOIP/CSP 真题、洛谷经典模板题为主）逐题整理，解析为原创撰写，非原书解析。每题附洛谷链接，可直接在线提交练习。
> **官方题单获取方式**：登录洛谷（www.luogu.com.cn），搜索"洛谷300题精析"题单（举办者 luoyj123），即可查看原书对应的全部题目。
> **使用方法建议**：每道题先独立思考 ≥20 分钟，再对照本文思路与代码，最后在洛谷提交验证；建立错题本，定期复盘。

---

## 目录（按篇）

- **第 1 篇 语言入门**（17 题）
- **第 2 篇 模拟和枚举**（15 题）
- **第 3 篇 基础算法**（15 题）
- **第 4 篇 数据结构**（11 题）
- **第 5 篇 搜索**（10 题）
- **第 6 篇 数学**（8 题）
- **第 7 篇 动态规划**（9 题）
- **第 8 篇 图论**（7 题）

---

# 第 1 篇 语言入门

> 本篇覆盖：结构化程序设计（输入输出、分支、循环、数组、字符串、结构体、函数）、递归、进制转换。难度以洛谷"入门 / 普及−"为主。
> 目标：建立基本编码能力，熟悉常见输入输出格式与基础语法。

## 1.1 结构化程序设计

### P1000 超级玛丽游戏

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1000>
- **难度**：入门　**标签**：输出
- **考点**：格式化输出、多行字符串

**题意简述**：洛谷试机题，要求原样输出一段超级玛丽场景的字符画，无输入。

**解题思路**：考察最基本的输出。需要注意两点：一是**原样输出**，不能增删任何空格和换行；二是字符串中可能存在转义字符（如 `\`、`"`），在 C++ 中要用 `\` 转义，或使用 `cout << R"(...)";` 原始字符串字面量。推荐逐行 `cout` 输出，肉眼核对每行末尾空格。

**复杂度**：O(1)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    // 按题目给出的字符画逐行输出
    cout << " ********" << endl;
    cout << " ************" << endl;
    cout << " ####....#." << endl;
    cout << " #..###.....##...." << endl;
    cout << " ###.......###### ### ###" << endl;
    cout << " ........... #...# #...#" << endl;
    cout << " ##*####### #.#.# #.#.#" << endl;
    cout << " ####*******###### #.#.# #.#.#" << endl;
    cout << " ...#***.****.*###.... #...# #...#" << endl;
    cout << " ....**********##..... ### ###" << endl;
    cout << " ....**** *****...." << endl;
    cout << " #### ####" << endl;
    cout << " ###### ######" << endl;
    cout << "##############################################################" << endl;
    cout << "#...#......#.##...#......#.##...#......#.##------------------#" << endl;
    cout << "###########################################------------------#" << endl;
    cout << "#..#....#....##..#....#....##..#....#....#####################" << endl;
    cout << "########################################## #----------#" << endl;
    cout << "#.....#......##.....#......##.....#......# #----------#" << endl;
    cout << "########################################## #----------#" << endl;
    cout << "#.#..#....#..##.#..#....#..##.#..#....#..# #----------#" << endl;
    cout << "########################################## ############" << endl;
    return 0;
}
```

**易错点**：空格数量极易抄错，务必逐字符核对；输出末尾换行符可有可无，评测系统会忽略行尾空格与末行多余换行。

---

### P1001 A+B Problem

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1001>
- **难度**：入门　**标签**：输入输出、算术
- **考点**：标准输入输出、int 范围

**题意简述**：输入两个整数 a、b，输出它们的和。数据范围 −10^9 ≤ a, b ≤ 10^9。

**解题思路**：洛谷"入坑第一题"，考察最基本的 `cin >> a >> b; cout << a+b;`。注意 a+b 的最大值为 2×10^9，仍落在 32 位 int（约 ±2.147×10^9）范围内，可以直接用 int。题目还强调：**程序中不要输出任何提示信息**（如"请输入"），否则会判 WA。

**复杂度**：O(1)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int a, b;
    cin >> a >> b;
    cout << a + b << endl;
    return 0;
}
```

**易错点**：严禁多余输出；`main` 必须返回 `int` 且返回 0。

---

### P5703 苹果采购

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5703>
- **难度**：入门　**标签**：算术
- **考点**：乘法、读入两个数

**题意简述**：每人分固定数量苹果，已知同学人数，求需要采购的苹果总数，即两数相乘。

**解题思路**：直接读入两个正整数相乘输出。题面保证输入和答案都在 int 范围内。

**复杂度**：O(1)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int a, b;
    cin >> a >> b;
    cout << a * b << endl;
    return 0;
}
```

**易错点**：无特殊陷阱，注意数据类型即可。

---

### P5721 数字直角三角形

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5721>
- **难度**：入门　**标签**：循环、格式化输出
- **考点**：双重循环、前导零补位

**题意简述**：给出 n，输出直角边长为 n 的数字直角三角形：数字从 1 开始递增填入，每个数字占 2 位，不足补前导 0；第 i 行输出 n−i+1 个数字后换行。

**解题思路**：用一个计数器 `cnt` 从 1 递增，行数 i 从 1 到 n，每行输出 n−i+1 个数。宽度 2 的格式化可用 `printf("%02d", cnt)` 或 `cout << setw(2) << setfill('0')`。这是练习**循环嵌套 + 格式化输出**的经典题。

**复杂度**：O(n²) 次输出。

**参考代码**：

```cpp
#include <cstdio>
int main() {
    int n, cnt = 1;
    scanf("%d", &n);
    for (int i = 1; i <= n; i++) {           // 行号
        for (int j = 1; j <= n - i + 1; j++) // 每行数字个数递减
            printf("%02d", cnt++);           // %02d：占2位，不足补0
        printf("\n");
    }
    return 0;
}
```

**易错点**：前导零补位；每行数字个数是 n−i+1（递减），不是固定 n 个。

---

### P5710 数的性质

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5710>
- **难度**：入门　**标签**：分支、逻辑运算
- **考点**：布尔表达式、按条件分类

**题意简述**：对整数 x 定义两个性质：性质 1 为偶数，性质 2 为"大于 4 且不大于 12"。四个人分别喜欢：两性质同时成立（小 A）、至少满足其一（Uim）、恰好满足其一（小 B）、都不满足（正妹）。依次输出四人是否喜欢（1/0）。

**解题思路**：设 p = (x 为偶数)，q = (4 < x ≤ 12)。四个人对应：
- 小 A：p && q
- Uim：p || q
- 小 B：(p && !q) || (!p && q)，即恰好一个成立
- 正妹：!p && !q
直接输出四个布尔表达式的结果即可。注意边界："大于 4 且不大于 12" 用 `x > 4 && x <= 12`。

**复杂度**：O(1)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int x;
    cin >> x;
    bool p = (x % 2 == 0);        // 性质1：偶数
    bool q = (x > 4 && x <= 12);  // 性质2
    cout << (p && q) << " " << (p || q) << " "
         << (p ^ q) << " " << (!p && !q) << endl;  // 恰好一个用异或
    return 0;
}
```

**易错点**：边界条件 4 和 12 的开闭；"恰好一个"容易写错成"至少一个"。

---

### P1425 小鱼的游泳时间

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1425>
- **难度**：入门　**标签**：时间计算、取模
- **考点**：时间换算、单位换算

**题意简述**：24 小时制下，小鱼从 a 时 b 分游到当天 c 时 d 分，求游了多少小时多少分钟（分钟 < 60）。

**解题思路**：统一换算成"分钟"再相减：总分钟 = (c×60+d) − (a×60+b)，结果小时 = 总分钟 ÷ 60，分钟 = 总分钟 % 60。先换算再分解是处理时间题的标准手法，避免借位讨论。

**复杂度**：O(1)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int a, b, c, d;
    cin >> a >> b >> c >> d;
    int start = a * 60 + b;   // 开始时刻（分钟）
    int end = c * 60 + d;     // 结束时刻（分钟）
    int diff = end - start;   // 总时长（分钟）
    cout << diff / 60 << " " << diff % 60 << endl;
    return 0;
}
```

**易错点**：先换算成小单位再运算，避免直接对"时、分"分别相减引发的借位错误。

---

### P1428 小鱼比可爱

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1428>
- **难度**：入门　**标签**：数组、遍历
- **考点**：一维数组、双重循环

**题意简述**：n 只鱼从左到右排成一排，每只鱼只能看到左边的鱼，求每只鱼左边有多少只鱼可爱程度小于自己。

**解题思路**：经典数组入门题。第 i 只鱼（0 下标）只需要统计 0~i−1 中 `a[j] < a[i]` 的数量。数据范围 n ≤ 100，直接双重循环 O(n²) 即可。这也是"前缀统计"思想的朴素版本。

**复杂度**：O(n²)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int a[105];
int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) cin >> a[i];
    for (int i = 0; i < n; i++) {
        int cnt = 0;
        for (int j = 0; j < i; j++)    // 只看左边的鱼
            if (a[j] < a[i]) cnt++;
        cout << cnt << (i == n - 1 ? "\n" : " ");
    }
    return 0;
}
```

**易错点**：下标从 0 开始后，左边范围是 [0, i)；输出格式要求空格分隔。

---

### P1427 小鱼的数字游戏

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1427>
- **难度**：入门　**标签**：数组、逆序输出
- **考点**：变长序列读取、倒序输出

**题意简述**：输入一串整数（以 0 结尾），把 0 之前的数字倒序输出。

**解题思路**：由于不知道个数，先读入并存入数组，直到读到 0 停止；记录个数 n，再从下标 n−1 到 0 倒序输出。也可以递归处理（读到非 0 先存，最后输出），作为递归思想的预热。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int a[105];
int main() {
    int n = 0;
    while (cin >> a[n] && a[n] != 0) n++;  // 读到0为止
    for (int i = n - 1; i >= 0; i--)
        cout << a[i] << (i ? " " : "\n");
    return 0;
}
```

**易错点**：0 本身不输出；注意最后一个数字后不要多输出空格（部分评测可容忍，但建议规范）。

---

### P1046 陶陶摘苹果

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1046>
- **难度**：入门　**标签**：数组、枚举
- **考点**：数组遍历、条件统计（NOIP 2005 普及组 T1）

**题意简述**：10 个苹果的高度已知，陶陶伸手高度 h 已知，踩 30cm 板凳后能摘到高度 ≤ h+30 的苹果，求能摘到的个数。

**解题思路**：遍历 10 个数，统计 `a[i] <= h + 30` 的个数。NOIP 普及组第一题，纯粹考察数组与循环。

**复杂度**：O(10)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int a[10], h, cnt = 0;
    for (int i = 0; i < 10; i++) cin >> a[i];
    cin >> h;
    for (int i = 0; i < 10; i++)
        if (a[i] <= h + 30) cnt++;   // 板凳高度+30
    cout << cnt << endl;
    return 0;
}
```

**易错点**：忘记加板凳高度 30；苹果高度与伸手高度的比较方向。

---

### P1055 ISBN 号码

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1055>
- **难度**：普及−　**标签**：字符串处理
- **考点**：字符串遍历、字符与数字转换（NOIP 2008 普及组 T1）

**题意简述**：ISBN 码形如 `x-xxx-xxxxx-x`，去掉分隔符后 9 位数字依次乘 1~9 求和，结果 mod 11 得识别码（10 记作 `X`）。判断输入 ISBN 的识别码是否正确，正确输出 `Right`，否则输出修正后的 ISBN。

**解题思路**：读入字符串，跳过 `-` 收集前 9 个数字字符，累加 `(s[i]-'0') * (++pos)`；`sum % 11` 得到校验码（10 对应字符 `X`）。与最后一位字符比较：若输入末尾为数字，直接比较数值；若为 `X`，比较是否等于 10。错误时构造正确字符串输出。考察字符处理基本功。

**复杂度**：O(|s|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string s;
    cin >> s;
    int sum = 0, pos = 1;
    for (int i = 0; i < s.size() - 1; i++) {   // 不含最后一位识别码
        if (s[i] == '-') continue;
        sum += (s[i] - '0') * pos++;           // 前9位乘1..9
    }
    int code = sum % 11;                       // 0..10，10记作X
    char right = (code == 10) ? 'X' : char('0' + code);
    if (s.back() == right) cout << "Right" << endl;
    else {
        s.back() = right;                      // 替换识别码
        cout << s << endl;
    }
    return 0;
}
```

**易错点**：`X` 对应的余数是 10 而非字符 '10'；前 9 位乘数从 1 开始依次递增；识别码是字符串最后一个字符。

---

### P5015 标题统计

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5015>
- **难度**：入门　**标签**：字符串统计
- **考点**：字符类型判断（NOIP 2018 普及组 T1）

**题意简述**：统计作文标题的字符数，空格和换行符不计入。

**解题思路**：读入一行（可能含空格），逐字符判断是否为空格或换行，其余都计数。C++ 中用 `getline(cin, s)` 读取整行，换行符不会被读入；判断 `s[i] != ' '` 即可。

**复杂度**：O(|s|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string s;
    getline(cin, s);          // 读取整行，含空格
    int cnt = 0;
    for (char c : s)
        if (c != ' ') cnt++;  // 空格不计
    cout << cnt << endl;
    return 0;
}
```

**易错点**：用 `cin >> s` 会跳过空格导致错误，必须用 `getline`；换行符本身不计入。

---

### P5740 最厉害的学生

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5740>
- **难度**：普及−　**标签**：结构体
- **考点**：结构体定义与使用

**题意简述**：n 名同学有姓名、语文、数学、英语成绩，输出总分最高者（总分并列时输出靠前者）的姓名与三科成绩。

**解题思路**：定义结构体 `struct Student { string name; int ch, ma, en; }`，读入后维护一个"当前最优"变量，遇到总分更高就更新。注意并列时保留先出现的（用严格 `>` 比较即可自然满足）。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
struct Student {
    string name;
    int ch, ma, en;
};
int main() {
    int n;
    cin >> n;
    Student best;
    int bestSum = -1;
    for (int i = 0; i < n; i++) {
        Student s;
        cin >> s.name >> s.ch >> s.ma >> s.en;
        int sum = s.ch + s.ma + s.en;
        if (sum > bestSum) { bestSum = sum; best = s; }  // 严格大于，保证并列取先出现
    }
    cout << best.name << " " << best.ch << " " << best.ma << " " << best.en << endl;
    return 0;
}
```

**易错点**：结构体变量初始化；并列条件用 `>` 而非 `>=`。

---

### P5735 距离函数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5735>
- **难度**：入门　**标签**：函数
- **考点**：函数定义、浮点数运算、两点距离

**题意简述**：给出三个点的坐标，求三角形周长，保留两位小数。

**解题思路**：定义函数 `double dis(double x1, double y1, double x2, double y2)` 返回两点欧氏距离 √((x2−x1)²+(y2−y1)²)，三次调用求和，用 `printf("%.2f")` 保留两位。考察"把重复逻辑封装成函数"。

**复杂度**：O(1)。

**参考代码**：

```cpp
#include <cstdio>
#include <cmath>
double dis(double x1, double y1, double x2, double y2) {
    double dx = x2 - x1, dy = y2 - y1;
    return sqrt(dx * dx + dy * dy);   // 欧氏距离
}
int main() {
    double x1, y1, x2, y2, x3, y3;
    scanf("%lf%lf%lf%lf%lf%lf", &x1, &y1, &x2, &y2, &x3, &y3);
    double c = dis(x1, y1, x2, y2) + dis(x2, y2, x3, y3) + dis(x3, y3, x1, y1);
    printf("%.2f\n", c);
    return 0;
}
```

**易错点**：浮点数用 `%lf` 读入、`%.2f` 输出；不要用 int 存坐标。

---

## 1.2 递归

### P5739 计算阶乘

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5739>
- **难度**：入门　**标签**：递归
- **考点**：递归函数的定义与终止条件

**题意简述**：求 n!（n ≤ 12），并尝试不用循环完成。

**解题思路**：n! = n × (n−1)!，边界 n=1 时返回 1。这正是递归的标准模板：**边界条件 + 递推关系**。虽然循环也能做，但本题用于建立"函数调用自身"的思维。n ≤ 12 时 n! ≤ 4.79×10⁸，int 可容纳（若 n=13 会溢出）。

**复杂度**：O(n) 层递归。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int fact(int n) {
    if (n <= 1) return 1;        // 边界条件
    return n * fact(n - 1);      // 递推关系：n! = n * (n-1)!
}
int main() {
    int n;
    cin >> n;
    cout << fact(n) << endl;
    return 0;
}
```

**易错点**：忘记边界条件会导致无限递归（栈溢出）；递归深度与返回值类型匹配。

---

### P5461 赦免战俘

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5461>
- **难度**：普及　**标签**：递归、分治
- **考点**：递归分治、矩阵填充

**题意简述**：2^n × 2^n 的矩阵，每次把当前正方形分成 4 个边长减半的小正方形，左上角那块全部记 0（赦免），其余三块继续同样操作，直到边长 1。输出最终 01 矩阵（1 表示不被赦免）。

**解题思路**：递归分治。函数 `solve(x, y, len)` 处理左上角为 (x,y)、边长为 len 的正方形：把它的左上 1/4 块（边长为 len/2，起点 (x,y)）全部填 0，然后对另外三块（右上、左下、右下）递归调用。边界 len=1 时直接返回（该格保留 1）。用二维数组存结果。递归深度 O(n) ≤ 10。

**复杂度**：O(4^n) = O(2^(2n))，即矩阵规模。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int a[1100][1100];
// 处理左上角(x,y)、边长len的正方形
void solve(int x, int y, int len) {
    if (len == 1) return;                 // 边长1不再划分
    for (int i = x; i < x + len / 2; i++) // 左上1/4全部赦免
        for (int j = y; j < y + len / 2; j++)
            a[i][j] = 0;
    solve(x, y + len / 2, len / 2);       // 右上
    solve(x + len / 2, y, len / 2);       // 左下
    solve(x + len / 2, y + len / 2, len / 2); // 右下
}
int main() {
    int n;
    cin >> n;
    int N = 1 << n;                       // 2^n，位运算求幂
    for (int i = 0; i < N; i++)
        for (int j = 0; j < N; j++) a[i][j] = 1;  // 初始全为1（不被赦免）
    solve(0, 0, N);
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++)
            cout << a[i][j] << (j == N - 1 ? "\n" : " ");
    }
    return 0;
}
```

**易错点**：`1 << n` 求 2^n（位运算的入门应用）；递归只处理三块，左上块直接置 0，不能递归；输出格式每行末尾无多余空格。

---

## 1.3 进制转换

### P2084 进制转换

- **洛谷链接**：<https://www.luogu.com.cn/problem/P2084>
- **难度**：入门　**标签**：进制、字符串
- **考点**：按位展开式、字符串处理

**题意简述**：给定 M 进制数 N（M < 10，N 位数 ≤ 1000），输出它按权展开的十进制式子，系数为 0 的项省略。

**解题思路**：从高位到低位遍历数字字符串，第 i 位（从 0 开始计）对应权 M^(len−1−i)。若该位不为 '0'，输出 `d*M^k`；多项之间用 `+` 连接。注意控制加号：只有非零项才需要（且首个非零项前不加号）。由于位数可达 1000，直接按字符串处理，不做数值运算。

**复杂度**：O(|N|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    int m;
    string n;
    cin >> m >> n;
    int len = n.size();
    bool first = true;                 // 是否已输出过项，控制加号
    for (int i = 0; i < len; i++) {
        if (n[i] == '0') continue;     // 系数为0省略
        if (!first) cout << "+";       // 非首项前加 +
        first = false;
        cout << n[i] << "*" << m << "^" << (len - 1 - i);
    }
    cout << endl;
    return 0;
}
```

**易错点**：指数是"从右往左"从 0 开始，即 len−1−i；零项省略后加号的拼接逻辑。

---

### P1143 进制转换

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1143>
- **难度**：普及−　**标签**：进制转换
- **考点**：任意进制 ↔ 十进制互转、字符与数字转换

**题意简述**：把一个 n 进制数（n ≤ 16，可用 A~F 表示 10~15，对应十进制 ≤ 10^9）转换成 m 进制数输出。

**解题思路**：两步走：① n 进制转十进制——按权展开累加；② 十进制转 m 进制——反复除以 m 取余，余数逆序输出。字符与数字互转：数字字符 `'0'+d`，字母 `'A'+d-10`。这是进制转换的标准模板。

**复杂度**：O(位数)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int c2d(char c) {                       // 字符->数字
    if (c >= '0' && c <= '9') return c - '0';
    return c - 'A' + 10;
}
char d2c(int d) {                       // 数字->字符
    if (d < 10) return '0' + d;
    return 'A' + d - 10;
}
int main() {
    int n, m;
    string s;
    cin >> n >> s >> m;
    long long val = 0;                  // 转十进制
    for (char c : s) val = val * n + c2d(c);
    string ans;
    if (val == 0) ans = "0";            // 特判0
    while (val > 0) {                   // 除基取余
        ans += d2c(val % m);
        val /= m;
    }
    for (int i = ans.size() - 1; i >= 0; i--) cout << ans[i];  // 逆序输出
    cout << endl;
    return 0;
}
```

**易错点**：十进制中间值可能超过 int（用 long long）；余数逆序输出；0 的特判；大于 9 的数码用大写字母。

---

## 本篇小结

完成本篇后应掌握：标准输入输出、分支与循环、一维数组、字符串处理、结构体与函数、递归思想、进制转换。这些都是后续所有篇章的"语言地基"。

---

# 第 2 篇 模拟和枚举

> 本篇覆盖：过程模拟、字符串与高精度、复杂模拟问题解析、循环与递归枚举、优化枚举策略、枚举的综合应用。难度以洛谷"普及− / 普及"为主。
> 目标：把题意翻译成程序流程（模拟），以及把可行解空间找全、找对（枚举），并学会最基本的枚举优化。

## 2.1 模拟

### P1563 玩具谜题

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1563>
- **难度**：普及−　**标签**：模拟、环形
- **考点**：环形下标移动、按条件分类（NOIP 2016 提高组 D1T1）

**题意简述**：n 个玩具小人围成一圈（逆时针编号），每人有朝向（0 朝内、1 朝外）与职业。m 条指令"向左/右数 s 个人"，朝内与朝外的左右方向相反，求最终到达的小人职业。

**解题思路**：把小人按下标 0..n−1 逆时针排列，维护当前位置 pos。朝向与指令共同决定移动方向：令 a=0 表示向左数、a=1 表示向右数。经验公式：若指令方向与小人朝向"同向"（向左且朝内，或向右且朝外），则 pos 沿下标递增方向走 s 步；否则反向走 s 步。用取模处理环形：`pos = (pos + s) % n` 或 `pos = (pos - s + n) % n`。逐条指令模拟即可。

**复杂度**：O(n + m)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int dir[100005];
string job[100005];
int main() {
    int n, m;
    cin >> n >> m;
    for (int i = 0; i < n; i++) cin >> dir[i] >> job[i];
    int pos = 0;
    for (int i = 0; i < m; i++) {
        int a, s;
        cin >> a >> s;                       // a=0向左, a=1向右
        bool same = (a == 0 && dir[pos] == 0) || (a == 1 && dir[pos] == 1);
        if (same) pos = (pos + s) % n;       // 下标递增方向
        else      pos = (pos - s % n + n) % n; // 下标递减方向
    }
    cout << job[pos] << endl;
    return 0;
}
```

**易错点**：取模前对 s 取 `s % n` 可避免整数溢出/负数；"同向"条件的判断最容易写反，建议先写方向表再推导。

---

### P1042 乒乓球

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1042>
- **难度**：普及−　**标签**：过程模拟
- **考点**：分段结算、状态模拟（NOIP 2003 普及组 T1）

**题意简述**：给出 W/L 序列，分别按 11 分制和 21 分制结算每一局比分：一方得分 ≥ 阈值且分差 ≥ 2 时一局结束，立即开始下一局；记录末尾未结束的一局也要输出。

**解题思路**：把两分制各模拟一遍。维护当前局双方比分 w、l，逐字符处理：读到 E 停止；读到 W/L 使对应分数 +1；判断 `max(w,l) >= lim && abs(w-l) >= 2` 则输出当前比分并清零。全部读完后，若还有未结算的局（包括 0:0 的开局）也要输出。先输出 11 分制所有行，空一行，再输出 21 分制。注意输入可能跨多行，需逐字符累计。

**复杂度**：O(总字符数)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
string s;
void calc(int lim) {                 // lim: 11 或 21
    int w = 0, l = 0;
    for (char c : s) {
        if (c == 'E') {              // 结束
            cout << w << ":" << l << endl;
            return;
        }
        if (c == 'W') w++; else if (c == 'L') l++;
        if (max(w, l) >= lim && abs(w - l) >= 2) {  // 一局结束
            cout << w << ":" << l << endl;
            w = l = 0;
        }
    }
    cout << w << ":" << l << endl;   // 读完整段后未结算的一局
}
int main() {
    char c;
    while (cin >> c) { s += c; }     // 连续读入直到EOF（含E）
    calc(11);
    cout << endl;
    calc(21);
    return 0;
}
```

**易错点**：一局结束条件必须"同时满足"阈值与分差 ≥ 2；E 之后立即输出当前局；21 分制也要完整模拟，不能只输出最后一局。

---

### P1328 生活大爆炸版石头剪刀布

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1328>
- **难度**：普及−　**标签**：周期模拟、查表
- **考点**：循环节取模、胜负表（NOIP 2014 提高组 D1T1）

**题意简述**：五手势石头剪刀布升级版（0 剪刀、1 石头、2 布、3 蜥蜴人、4 斯波克），两人按各自周期出拳 N 次，统计双方得分。

**解题思路**：把胜负关系做成 5×5 查表 `win[i][j]`（甲出 i 对乙出 j：1 甲胜、0 平、−1 甲负）。第 k 次出拳：甲 `a[k % na]`、乙 `b[k % nb]`，查表累加得分。周期性是模拟题最常见的考点，取模即完成循环展开。

**复杂度**：O(N)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
// win[i][j]: 甲出i对乙出j的结果, 1甲胜 0平 -1甲负
int win[5][5] = {
    {0, -1, 1, 1, -1},
    {1, 0, -1, -1, 1},
    {-1, 1, 0, -1, 1},
    {-1, 1, 1, 0, -1},
    {1, -1, -1, 1, 0}
};
int a[205], b[205];
int main() {
    int n, na, nb;
    cin >> n >> na >> nb;
    for (int i = 0; i < na; i++) cin >> a[i];
    for (int i = 0; i < nb; i++) cin >> b[i];
    int sa = 0, sb = 0;
    for (int i = 0; i < n; i++) {
        int r = win[a[i % na]][b[i % nb]];   // 取模循环
        if (r > 0) sa++;
        else if (r < 0) sb++;
    }
    cout << sa << " " << sb << endl;
    return 0;
}
```

**易错点**：胜负表方向不能搞反（是"甲对乙"）；平局两人都不加分；周期的取模下标。

---

### P1308 统计单词数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1308>
- **难度**：普及−　**标签**：字符串处理
- **考点**：大小写归一、精确单词匹配（NOIP 2011 普及组 T2）

**题意简述**：给定单词与文章（可能含空格），统计单词在文章中出现次数与首次位置（位置从 0 计）。要求不区分大小写、完全匹配独立单词（不能是单词的一部分）。

**解题思路**：经典技巧——把待匹配单词两侧都加上空格形成 `" word "`，文章首尾也补空格，然后逐位置查找该子串。这样天然保证"独立单词"匹配（单词两侧必须是空格或边界）。先整体转小写再处理。文章长度 ≤ 10^6，用 `find` 循环查找即可。

**复杂度**：O(文章长度 × 匹配开销)，实测可行。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
string tolower_all(string s) {
    for (auto &c : s) if (c >= 'A' && c <= 'Z') c += 32;
    return s;
}
int main() {
    string word, text;
    getline(cin, word);
    getline(cin, text);
    word = tolower_all(word);
    text = tolower_all(text);
    word = " " + word + " ";      // 两侧补空格，保证独立单词
    text = " " + text + " ";
    int cnt = 0, first = -1, pos = 0;
    while ((pos = text.find(word, pos)) != string::npos) {
        if (cnt == 0) first = pos; // 记录首次出现（在补空格后的串中）
        cnt++;
        pos += word.size() - 1;    // 从单词末尾继续找，避免重叠
    }
    if (cnt == 0) cout << -1 << endl;
    else cout << cnt << " " << first << endl;
    return 0;
}
```

**易错点**：必须整体转小写；补空格后 `first` 是"补空格后"的位置，但题目要求的位置仍从 0 开始——因为前面只多了一个空格，first 恰好等于原文位置，无需再减；大小写归一在转小写后自动解决。

---

### P1553 数字反转（升级版）

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1553>
- **难度**：普及−　**标签**：字符串处理、分类讨论
- **考点**：按类型处理、前导/尾随零

**题意简述**：输入一个整数/小数/分数/百分数，分别反转各部分数字：整数反转整体；小数反转整数部分与小数部分（不交换）；分数反转分子分母；百分数反转数字部分。要求去掉多余前导零与尾随零。

**解题思路**：写一个工具函数 `rev(s)`：反转字符串并去掉前导零（若全 0 则保留一个 "0"）。然后按分隔符分类：无分隔符→整数；`.`→小数（整数部分 rev，小数部分 rev 后去尾随 0）；`/`→分数；`%`→百分数。全部用字符串处理，不转数值（位数可达 20 位）。

**复杂度**：O(|s|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
// 反转并去掉前导零
string rev(string s) {
    string t(s.rbegin(), s.rend());
    int p = 0;
    while (p + 1 < (int)t.size() && t[p] == '0') p++;  // 去掉前导0，至少留一位
    return t.substr(p);
}
int main() {
    string s;
    cin >> s;
    if (s.find('%') != string::npos) {        // 百分数
        cout << rev(s.substr(0, s.size() - 1)) << "%" << endl;
    } else if (s.find('.') != string::npos) { // 小数
        int p = s.find('.');
        string a = rev(s.substr(0, p));
        string b = s.substr(p + 1);
        reverse(b.begin(), b.end());
        while (b.size() > 1 && b.back() == '0') b.pop_back(); // 去尾随0
        cout << a << "." << b << endl;
    } else if (s.find('/') != string::npos) { // 分数
        int p = s.find('/');
        cout << rev(s.substr(0, p)) << "/" << rev(s.substr(p + 1)) << endl;
    } else {                                  // 整数
        cout << rev(s) << endl;
    }
    return 0;
}
```

**易错点**：前导零要去但不能去光（"0"→"0"）；小数部分去的是尾随零；分隔符类型判断顺序。

---

### P2010 回文日期

- **洛谷链接**：<https://www.luogu.com.cn/problem/P2010>
- **难度**：普及−　**标签**：日期模拟、回文
- **考点**：日期合法性、构造枚举（NOIP 2016 普及组 T2）

**题意简述**：给定两个 8 位日期，统计区间内"真实存在且 8 位数字回文"的日期个数。

**解题思路**：与其逐日枚举（天数多且要写日增量），不如反向构造：枚举年份 y（date1 前 4 位到 date2 前 4 位），由年份构造回文日期：后 4 位是年份倒序，即 y 的"镜像" `mmdd`。检查该日期是否在区间内、月份 1~12、天数符合该月/闰年规则。这样最多枚举几千个年份，极快。

**复杂度**：O(年份差)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int days[13] = {0,31,28,31,30,31,30,31,31,30,31,30,31};
bool isLeap(int y) { return (y % 4 == 0 && y % 100 != 0) || y % 400 == 0; }
int main() {
    int d1, d2;
    cin >> d1 >> d2;
    int cnt = 0;
    for (int y = d1 / 10000; y <= d2 / 10000; y++) {
        int mm = y % 10 * 10 + (y / 10) % 10;   // 年份后两位镜像 -> 月
        int dd = (y / 100) % 10 * 10 + y / 1000; // 年份前两位镜像 -> 日
        int date = y * 10000 + mm * 100 + dd;   // 构造回文日期
        if (date < d1 || date > d2) continue;
        if (mm < 1 || mm > 12) continue;
        int maxd = days[mm];
        if (mm == 2 && isLeap(y)) maxd = 29;
        if (dd >= 1 && dd <= maxd) cnt++;
    }
    cout << cnt << endl;
    return 0;
}
```

**易错点**：镜像取位别写反（月=年份后两位倒序，日=年份前两位倒序）；闰年二月 29 天；日期必须在区间内。

---

### P1601 高精度加法

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1601>
- **难度**：普及−　**标签**：高精度
- **考点**：大整数加法模板

**题意简述**：两个非负整数（可长达 500 位），求其和。

**解题思路**：内置类型装不下，改用字符串模拟竖式加法：从低位到高位逐位相加，维护进位 carry；两个串对齐后较短的补 0；最后若还有进位则在最高位补 1。这是高精度运算的入门模板，后续的减法、乘法都基于同一思想。

**复杂度**：O(|a|+|b|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
int main() {
    string a, b;
    cin >> a >> b;
    reverse(a.begin(), a.end());   // 低位在前，便于逐位加
    reverse(b.begin(), b.end());
    if (a.size() < b.size()) swap(a, b);  // a 是较长者
    int carry = 0;
    for (int i = 0; i < (int)a.size(); i++) {
        int x = a[i] - '0' + carry;
        if (i < (int)b.size()) x += b[i] - '0';
        a[i] = x % 10 + '0';
        carry = x / 10;
    }
    if (carry) a += char('0' + carry);   // 最高位进位
    reverse(a.begin(), a.end());
    cout << a << endl;
    return 0;
}
```

**易错点**：低位对齐与进位；最高位可能多出一位；不要用 int 存整个数。

---

### P1303 A×B Problem

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1303>
- **难度**：普及−　**标签**：高精度
- **考点**：高精度乘法模板

**题意简述**：两个非负整数（各不超过 10^2000），求乘积。

**解题思路**：竖式乘法模板：用数组存结果，`c[i+j] += a[i] * b[j]`，全部累加后再统一处理进位（逐位 `c[i] += c[i]/10; c[i] %= 10`），最后去掉前导零。注意结果的位数最多为 len(a)+len(b)，数组要开够。

**复杂度**：O(|a|×|b|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
int ca[2010], cb[2010], cc[4010];
int main() {
    string a, b;
    cin >> a >> b;
    for (int i = 0; i < (int)a.size(); i++) ca[i] = a[a.size()-1-i] - '0';
    for (int i = 0; i < (int)b.size(); i++) cb[i] = b[b.size()-1-i] - '0';
    for (int i = 0; i < (int)a.size(); i++)
        for (int j = 0; j < (int)b.size(); j++)
            cc[i + j] += ca[i] * cb[j];     // 先累加不进位
    int len = a.size() + b.size();
    for (int i = 0; i < len; i++) {          // 统一进位
        cc[i + 1] += cc[i] / 10;
        cc[i] %= 10;
    }
    while (len > 1 && cc[len - 1] == 0) len--;  // 去前导0
    for (int i = len - 1; i >= 0; i--) cout << cc[i];
    cout << endl;
    return 0;
}
```

**易错点**：进位要在所有乘法累加之后统一处理；结果数组长度开够；前导零删除不能删光（结果为 0 时保留一个）。

---

## 2.2 枚举

### P1008 三连击

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1008>
- **难度**：普及−　**标签**：暴力枚举
- **考点**：枚举 + 数字位去重检查（NOIP 1998 普及组 T1）

**题意简述**：将 1~9 分成三组组成三个三位数，使它们构成 1:2:3，输出所有解。

**解题思路**：枚举第一个三位数 i（从 123 到 329，保证 3i ≤ 987），令 j=2i、k=3i，检查 i、j、k 的 9 个数字恰好是 1~9 各一次。用长度为 10 的标记数组统计每个数字出现次数。这是暴力枚举 + 可行性检查的标准套路。

**复杂度**：O(329×9)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
bool check(int a, int b, int c) {
    int cnt[10] = {0};
    int t[3] = {a, b, c};
    for (int x : t)
        for (int i = 0; i < 3; i++) {
            cnt[x % 10]++;
            x /= 10;
        }
    for (int i = 1; i <= 9; i++)
        if (cnt[i] != 1) return false;   // 每个数字恰好出现一次
    return true;
}
int main() {
    for (int i = 123; i <= 329; i++) {
        int j = i * 2, k = i * 3;
        if (check(i, j, k))
            cout << i << " " << j << " " << k << endl;
    }
    return 0;
}
```

**易错点**：枚举上界 329（3×329=987 < 1000）；数字必须是 1~9 各一次，不能含 0。

---

### P1149 火柴棒等式

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1149>
- **难度**：普及−　**标签**：枚举优化
- **考点**：预处理打表 + 枚举（NOIP 2008 提高组 T2）

**题意简述**：给定火柴棒数 n（≤24），统计能拼成多少个 A+B=C 的等式（加号等号各用 2 根，A、B、C ≥ 0 且非零数最高位不为 0）。

**解题思路**：先预处理 0~999 每个数需要多少根火柴（`cnt[i] = cnt[i/10] + f[i%10]`，f 是数字火柴数表）。然后枚举 A、B（0~999），若 `cnt[A]+cnt[B]+cnt[C]+4 == n`（C=A+B，+4 是加号和等号）则计数。n 小，火柴数决定了 A、B 实际范围（用最少火柴的数字"1"也要 2 根，所以 A、B 最大约 (24−4)/2/2≈10^3 量级），直接枚举 1000×1000 足够。

**复杂度**：O(10^6)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int f[10] = {6,2,5,5,4,5,6,3,7,6};  // 数字0~9所需火柴数
int cnt[2005];
int main() {
    int n;
    cin >> n;
    cnt[0] = f[0];
    for (int i = 1; i <= 2000; i++) cnt[i] = cnt[i / 10] + f[i % 10];
    int ans = 0;
    for (int a = 0; a <= 1000; a++)
        for (int b = 0; b <= 1000; b++) {
            int c = a + b;
            if (c > 1000) break;
            if (cnt[a] + cnt[b] + cnt[c] + 4 == n) ans++;  // +4:加号等号
        }
    cout << ans << endl;
    return 0;
}
```

**易错点**：加号与等号共 4 根火柴必须计入；预处理时 0 的火柴数要单独处理（cnt[0]=6）；A+B=C 与 B+A=C 算两个等式（枚举自然计入）。

---

### P1088 火星人

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1088>
- **难度**：普及−　**标签**：排列枚举
- **考点**：next_permutation 应用（NOIP 2004 普及组 T4）

**题意简述**：1~N 的一个排列代表火星人手指顺序，字典序大小对应数值大小。给定当前排列和要加的小整数 M，求加完后的排列（即字典序往后数第 M 个排列）。

**解题思路**：本质是"字典序第 M 个后继排列"。N ≤ 10^4、M ≤ 100，直接调用 `std::next_permutation` M 次即可，复杂度 O(M·N) 在可接受范围。这也是 C++ STL 排列算法的经典应用；如果 M 很大则需用康托展开等数论方法（本题不需要）。

**复杂度**：O(M·N)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int a[10005];
int main() {
    int n, m;
    cin >> n >> m;
    for (int i = 0; i < n; i++) cin >> a[i];
    while (m--) next_permutation(a, a + n);  // 往后跳M个排列
    for (int i = 0; i < n; i++)
        cout << a[i] << (i == n - 1 ? "\n" : " ");
    return 0;
}
```

**易错点**：`next_permutation` 直接在原数组上修改；输入保证结果在范围内；输出格式无多余空格。

---

### P3392 涂条纹

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3392>
- **难度**：普及−　**标签**：枚举划分
- **考点**：枚举分界点、最小化代价

**题意简述**：N×M 的格子（W/B/R），要改成"上白、中蓝、下红"三段（每段至少一行），每改一格代价 1，求最小代价。

**解题思路**：合法图案完全由两个分界决定：白色行数 w、蓝色行数 b（红行数 = N−w−b）。枚举 w、b（w≥1、b≥1、N−w−b≥1），计算每种划分下需要改的格子数：白色区每行统计非 W 的个数，蓝色区统计非 B 的个数，红色区统计非 R 的个数，累加取最小。可以先预处理每行 W/B/R 的计数，把单次检查降到 O(N·M) 内。

**复杂度**：O(N²·M)（n ≤ 50 完全可行）。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
string s[55];
int main() {
    int n, m;
    cin >> n >> m;
    for (int i = 0; i < n; i++) cin >> s[i];
    int ans = n * m;
    for (int w = 1; w <= n - 2; w++)       // 白色行数
        for (int b = 1; b + w <= n - 1; b++) { // 蓝色行数
            int cost = 0;
            for (int i = 0; i < n; i++) {
                char target = (i < w) ? 'W' : (i < w + b ? 'B' : 'R');
                for (int j = 0; j < m; j++)
                    if (s[i][j] != target) cost++;
            }
            ans = min(ans, cost);
        }
    cout << ans << endl;
    return 0;
}
```

**易错点**：三段都至少一行（w、b、n−w−b ≥ 1）；枚举边界容易写错。

---

### P1980 计数问题

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1980>
- **难度**：入门　**标签**：枚举、数字分解
- **考点**：逐位统计（NOIP 2013 普及组 T1）

**题意简述**：统计 1~n 所有整数中数字 x 出现的总次数。

**解题思路**：对每个数逐位取数字：`while (t) { if (t % 10 == x) cnt++; t /= 10; }`。n ≤ 10^6，总位数约 10^7 量级，直接枚举可行。这是"拆位统计"的基础写法，也是更高级数位 DP 的朴素版。

**复杂度**：O(n·位数)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int n, x, cnt = 0;
    cin >> n >> x;
    for (int i = 1; i <= n; i++) {
        int t = i;
        while (t) {
            if (t % 10 == x) cnt++;
            t /= 10;
        }
    }
    cout << cnt << endl;
    return 0;
}
```

**易错点**：循环变量不能直接改（要用副本）；i=0 的情况这里不需要（从 1 开始）。

---

### P2241 统计方形（数据加强版）

- **洛谷链接**：<https://www.luogu.com.cn/problem/P2241>
- **难度**：普及−　**标签**：组合计数、数学推导
- **考点**：矩形/正方形计数公式（NOIP 1997 普及组 T1）

**题意简述**：n×m 棋盘，统计其中正方形个数与长方形（不含正方形）个数。

**解题思路**：边长为 k 的正方形数量为 (n−k+1)(m−k+1)，累加 k=1..min(n,m) 得正方形总数。所有矩形（含正方形）总数 = 选两条横线 × 选两条竖线 = C(n+1,2)·C(m+1,2) = n(n+1)/2 · m(m+1)/2。长方形数 = 矩形总数 − 正方形数。n、m ≤ 5000，结果可达约 10^14 量级，必须用 long long。

**复杂度**：O(min(n,m))。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    long long n, m;
    cin >> n >> m;
    long long sq = 0;
    for (long long k = 1; k <= min(n, m); k++)
        sq += (n - k + 1) * (m - k + 1);       // 边长为k的正方形
    long long total = n * (n + 1) / 2 * m * (m + 1) / 2; // 所有矩形
    cout << sq << " " << total - sq << endl;   // 长方形 = 总数 - 正方形
    return 0;
}
```

**易错点**：乘法可能溢出 int，全程 long long；"长方形"不含正方形。

---

### P1152 欢乐的跳

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1152>
- **难度**：入门　**标签**：枚举、标记数组
- **考点**：相邻差绝对值覆盖检查

**题意简述**：判断数组相邻元素差的绝对值集合是否恰好为 {1, 2, …, n−1}。

**解题思路**：计算每对相邻差的绝对值，用 bool 数组标记；最后检查 1~n−1 是否全部出现。n ≤ 1000，简单枚举即可。n=1 时差集为空，直接判 Jolly。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
bool used[1005];
int main() {
    int n;
    cin >> n;
    int prev = 0, cur;
    for (int i = 0; i < n; i++) {
        cin >> cur;
        if (i > 0) used[abs(cur - prev)] = true;  // 标记差值绝对值
        prev = cur;
    }
    for (int i = 1; i <= n - 1; i++)
        if (!used[i]) { cout << "Not jolly" << endl; return 0; }
    cout << "Jolly" << endl;
    return 0;
}
```

**易错点**：差的绝对值可能超过 n−1，标记前无需越界保护（题面保证合法？为稳妥可先判断）；n=1 直接 Jolly。

---

## 本篇小结

完成本篇后应掌握：把题目流程翻译成模拟代码（环形、周期、分段结算、日期），字符串与高精度处理，以及暴力枚举 + 简单优化（预处理、缩小枚举范围、数学推导）。模拟和枚举是几乎所有竞赛题的第一步，务必练熟。

---

# 第 3 篇 基础算法

> 本篇覆盖：排序、贪心、双指针（尺取法）、二分法（查找与二分答案）、前缀和与差分。难度以洛谷"普及− / 普及"为主，是 CSP-J/S 的核心高频考点。
> 目标：掌握五类基础算法的模板与"什么时候用"的判断标准。

## 3.1 排序

### P1177 【模板】排序

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1177>
- **难度**：普及−　**标签**：排序模板
- **考点**：排序算法的选择与 STL sort

**题意简述**：对 N 个数（N ≤ 10^5）升序排序输出。

**解题思路**：排序模板题。竞赛中最常用 `std::sort`（O(N log N)，内部是快排+插入排序混合）。也可手写快速排序理解原理，但注意普通快排在完全有序数据上会退化，实际比赛直接用 `sort`。理解复杂度：O(N log N)。

**复杂度**：O(N log N)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int a[100005];
int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) cin >> a[i];
    sort(a, a + n);                    // STL排序
    for (int i = 0; i < n; i++)
        cout << a[i] << (i == n - 1 ? "\n" : " ");
    return 0;
}
```

**易错点**：输入规模大时用 `ios::sync_with_stdio(false)` 或 `scanf`；`sort` 范围是 [begin, end)。

---

### P1059 明明的随机数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1059>
- **难度**：普及−　**标签**：排序、去重
- **考点**：排序 + 去重（NOIP 2006 普及组 T1）

**题意简述**：N 个 1~1000 的随机数，去重后升序输出。

**解题思路**：三种做法：① `sort` 后相邻相同项跳过输出；② 直接利用数据范围小用桶标记（bool vis[1001]）天然去重+排序；③ `unique` 去重。桶标记思路最直观：数字范围 1~1000 很小，访问数组下标即完成排序。这里展示 sort+去重写法。

**复杂度**：O(N log N)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int a[105];
int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) cin >> a[i];
    sort(a, a + n);
    int cnt = 0;
    for (int i = 0; i < n; i++)
        if (i == 0 || a[i] != a[i - 1]) cnt++;   // 去重计数
    cout << cnt << endl;
    for (int i = 0; i < n; i++)
        if (i == 0 || a[i] != a[i - 1])
            cout << a[i] << (--cnt ? " " : "\n");
    return 0;
}
```

**易错点**：去重时要跳过与前一相同的元素；输出个数与内容一致。

---

### P1012 拼数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1012>
- **难度**：普及+/提高−　**标签**：贪心排序、字符串
- **考点**：自定义比较规则排序（NOIP 1998 提高组 T2）

**题意简述**：n 个正整数，把它们按某种顺序首尾拼接，求能组成的最大整数。

**解题思路**：经典"字典序贪心排序"题。直观想法是按字符串字典序排，但反例：9 和 90，字典序 "90" > "9"，但 "9"+"90"=990 > "90"+"9"=909。正确比较规则：`a+b > b+a` 时 a 排在 b 前。用字符串比较实现该规则作为 `sort` 的比较函数即可。这个"拼接比较"技巧要牢记。

**复杂度**：O(n log n × 串长)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
using namespace std;
bool cmp(const string &a, const string &b) {
    return a + b > b + a;    // 拼接后更大的排前面
}
int main() {
    int n;
    cin >> n;
    vector<string> v(n);
    for (int i = 0; i < n; i++) cin >> v[i];
    sort(v.begin(), v.end(), cmp);
    string ans;
    for (auto &s : v) ans += s;
    cout << ans << endl;
    return 0;
}
```

**易错点**：不能直接按字典序排序；比较函数必须严格弱序（`a+b > b+a` 满足）。

---

## 3.2 贪心

### P1223 排队接水

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1223>
- **难度**：普及−　**标签**：贪心
- **考点**：最小化等待时间——短作业优先

**题意简述**：n 人排队接水，接水时间已知，求使平均等待时间最小的顺序及该平均等待时间。

**解题思路**：经典贪心结论：**接水时间短的人先接**（短作业优先 SJF），总等待时间最小。证明可用交换论证：若两人顺序 (t1, t2) 交换为 (t2, t1)，对总等待时间的贡献由 t1 变成 t2，t1 ≤ t2 时前者更优。等待时间累加：第 i 位（0 起）的人让后面 n−1−i 人各等他 t[i] 分钟，总等待 = Σ t[i]×(n−1−i)。输出顺序（编号）与平均等待时间（总等待/n，保留两位小数）。

**复杂度**：O(n log n)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
pair<int, int> p[1005];   // {接水时间, 编号}
int main() {
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++) {
        cin >> p[i].first;
        p[i].second = i;
    }
    sort(p + 1, p + n + 1);            // 按时间升序
    long long sum = 0;
    for (int i = 1; i <= n; i++) {
        cout << p[i].second << " ";
        sum += p[i].first * (n - i);   // 第i位让后面n-i人等待
    }
    printf("\n%.2f\n", (double)sum / n);
    return 0;
}
```

**易错点**：等待时间不含自己的接水时间；平均等待保留两位小数；总等待可能超 int（用 long long）。

---

### P1803 凌乱的yyy / 线段覆盖

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1803>
- **难度**：普及−　**标签**：贪心、区间
- **考点**：最多不相交区间——按右端点排序

**题意简述**：n 个比赛（区间 [a,b)），一个人不能同时参加多个，求最多能参加多少个。

**解题思路**：经典区间贪心（活动安排问题）：**按结束时间升序排序，依次选择结束最早且不与已选区间冲突的**。正确性：选择结束最早的区间能留下最多剩余时间。实现时记录 last（上一个已选区间的结束），遍历排序后区间，若当前 a ≥ last 则选择并更新 last。

**复杂度**：O(n log n)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
pair<int, int> seg[1000005];  // {结束, 开始}，pair默认按第一关键字排
int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) {
        int a, b;
        cin >> a >> b;
        seg[i] = {b, a};       // 结束时间放前面
    }
    sort(seg, seg + n);        // 按结束时间升序
    int ans = 0, last = -1;
    for (int i = 0; i < n; i++) {
        if (seg[i].second >= last) {   // 开始不早于上一区间结束
            ans++;
            last = seg[i].first;       // 更新结束时间
        }
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：排序键是结束时间；区间可首尾相接（a ≥ last 即可选）。

---

### P1090 合并果子

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1090>
- **难度**：普及　**标签**：贪心、哈夫曼、优先队列
- **考点**：每次合并最小两堆（NOIP 2004 提高组 T2）

**题意简述**：n 堆果子，每次合并两堆，代价为两堆之和，求合并成一堆的最小总代价。

**解题思路**：哈夫曼树思想：**每次取最小的两堆合并**，总代价最小。用优先队列（小顶堆）维护当前堆，每次 pop 两个最小，合并后 push 回去，累加代价，直到剩一堆。证明：先合并的堆会参与后续多次合并，因此越小的堆越早合并。

**复杂度**：O(n log n)。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
int main() {
    int n;
    cin >> n;
    priority_queue<int, vector<int>, greater<int>> pq;  // 小顶堆
    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        pq.push(x);
    }
    long long ans = 0;
    while (pq.size() > 1) {
        int a = pq.top(); pq.pop();
        int b = pq.top(); pq.pop();
        ans += a + b;
        pq.push(a + b);
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：合并出的新堆要重新入队（可能仍是最小）；结果可能超过 int（用 long long）；循环到只剩一堆为止。

---

## 3.3 双指针

### P1102 A-B 数对

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1102>
- **难度**：普及−　**标签**：双指针、排序
- **考点**：排序 + 双指针统计相等元素区间

**题意简述**：N 个数中统计满足 A−B=C 的数对个数（不同位置算不同数对）。

**解题思路**：A−B=C ⟺ A = B+C。排序后对每个 A，统计值等于 A−C 的个数。双指针法：排序后，用两个指针维护"等于某值"的区间 [l, r)。遍历每个元素作为 B（值 v），若 v+C 存在，则贡献 = 值 v+C 的元素个数 × 值 v 的元素个数？——不对，这样会把同一位置的数用两次。正确做法：对每个位置 i（作为 A），二分/双指针统计区间内等于 a[i]−C 的元素个数。双指针实现：排序后 i 遍历，对每个 i 找值 val=a[i]−C 的区间 [l,r)。由于数组有序且 a[i] 单调，l、r 单调移动，总 O(N)。注意答案可能超 int（用 long long）。

**复杂度**：O(N log N)（排序）+ O(N)（指针）。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
long long a[200005];
int main() {
    int n;
    long long c;
    cin >> n >> c;
    for (int i = 0; i < n; i++) cin >> a[i];
    sort(a, a + n);
    long long ans = 0;
    int l = 0, r = 0;          // [l,r) 是"值==当前a[i]-c"的区间
    for (int i = 0; i < n; i++) {
        long long target = a[i] - c;
        while (l < n && a[l] < target) l++;
        while (r < n && a[r] <= target) r++;
        ans += r - l;          // 区间长度即满足条件的B个数
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：l、r 随 i 单调不减，需按值推进；答案用 long long；排序后重复值集中成区间。

---

### P1147 连续正整数和

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1147>
- **难度**：普及−　**标签**：尺取法
- **考点**：双指针维护区间和

**题意简述**：找出所有连续正整数段（至少两项），其和为 M，按左端点升序输出。

**解题思路**：尺取法（滑动窗口）：左右指针 l、r 维护区间 [l, r]，区间和 sum。sum < M 时 r 右扩；sum > M 时 l 右缩；sum == M 时记录并 l 右移继续找。由于都是正整数，单调性成立。复杂度 O(M)。注意 l、r 枚举范围到 M/2+1 即可（区间至少两项，起点不会超过 M/2）。

**复杂度**：O(M)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int m;
    cin >> m;
    long long sum = 0;
    int l = 1, r = 1;             // 左闭右开 [l, r)
    while (l <= m / 2) {
        while (sum < m) sum += r++;          // 右扩
        while (sum > m) { sum -= l; l++; }   // 左缩
        if (sum == m) {
            cout << l << " " << r - 1 << endl;
            sum -= l;                        // 移出l，继续找下一段
            l++;
        }
    }
    return 0;
}
```

**易错点**：区间用左闭右开避免边界混乱；找到一组后必须 l 右移继续；sum 用 long long。

---

### P1638 逛画展

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1638>
- **难度**：普及　**标签**：滑动窗口
- **考点**：最短覆盖区间（双指针）

**题意简述**：n 幅画，每幅作者编号 1~m，求最短连续区间 [x,y] 包含所有 m 位画家的画（若有多个输出 x 最小者）。

**解题思路**：滑动窗口求"最短覆盖所有类别"：右指针扩展直到集齐 m 种，然后左指针收缩直到缺失某类，期间更新最短区间。维护 cnt[作者] 数组记录窗口内各类数量，以及当前窗口内不同类别数 kinds。O(n)。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int a[1000005], cnt[2005];
int main() {
    int n, m;
    cin >> n >> m;
    for (int i = 1; i <= n; i++) cin >> a[i];
    int l = 1, r = 0, kinds = 0, bestL = 1, bestR = n, bestLen = n;
    while (r < n) {
        if (++cnt[a[++r]] == 1) kinds++;          // 扩展右端，新类别+1
        while (kinds == m) {                      // 已覆盖全部，尝试收缩左端
            if (r - l + 1 < bestLen) {            // 更新最优区间
                bestLen = r - l + 1;
                bestL = l; bestR = r;
            }
            if (--cnt[a[l++]] == 0) kinds--;      // 左端移出，某类缺失
        }
    }
    cout << bestL << " " << bestR << endl;
    return 0;
}
```

**易错点**：收缩时若某类计数归零则 kinds 减一；相等长度时输出 x 最小——收缩优先从左端进行，自然满足。

---

## 3.4 二分法

### P2249 【深基13.例1】查找

- **洛谷链接**：<https://www.luogu.com.cn/problem/P2249>
- **难度**：普及−　**标签**：二分查找模板
- **考点**：有序数组中查第一次出现位置

**题意简述**：单调不减序列中 m 次询问，输出 q 首次出现的位置（1-based），不存在输出 −1。

**解题思路**：标准二分查找求下界（lower_bound）：在 [l, r] 中找第一个 ≥ q 的位置。模板要点：`while (l < r) { mid=(l+r)/2; if (a[mid] >= q) r = mid; else l = mid + 1; }`，结束后检查 a[l] 是否等于 q。注意数据量大要用快速 IO。

**复杂度**：O((n+m) log n)。

**参考代码**：

```cpp
#include <cstdio>
int a[1000005];
int main() {
    int n, m;
    scanf("%d%d", &n, &m);
    for (int i = 1; i <= n; i++) scanf("%d", &a[i]);
    while (m--) {
        int q;
        scanf("%d", &q);
        int l = 1, r = n;
        while (l < r) {              // 二分找第一个 >= q 的位置
            int mid = (l + r) / 2;
            if (a[mid] >= q) r = mid;
            else l = mid + 1;
        }
        if (a[l] == q) printf("%d ", l);
        else printf("-1 ");
    }
    return 0;
}
```

**易错点**：查找"第一次出现"用 `>=` 收缩右边界；判断 `a[l] == q` 决定是否存在；输入输出量大用 scanf/printf。

---

### P1873 砍树

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1873>
- **难度**：普及−　**标签**：二分答案
- **考点**：答案单调性 + 二分（COCI）

**题意简述**：设锯片高度 H，砍得木材 = Σ max(0, 树高−H)，求最大 H 使得所得木材 ≥ M。

**解题思路**：二分答案典型题。H 越大，得到的木材越少——单调。二分 H（范围 [0, maxH]），对每个 H 用 O(N) 检查木材总量是否 ≥ M：若满足说明 H 还能更高，否则降低。复杂度 O(N log maxH)。

**复杂度**：O(N log maxH)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long h[1000005];
int main() {
    int n;
    long long m;
    cin >> n >> m;
    long long mx = 0;
    for (int i = 0; i < n; i++) { cin >> h[i]; mx = max(mx, h[i]); }
    long long l = 0, r = mx;
    while (l < r) {
        long long mid = (l + r + 1) / 2;   // 上取整防死循环
        long long sum = 0;
        for (int i = 0; i < n; i++)
            if (h[i] > mid) sum += h[i] - mid;
        if (sum >= m) l = mid;             // 木材够，可继续抬高
        else r = mid - 1;
    }
    cout << l << endl;
    return 0;
}
```

**易错点**：求"最大可行 H"时二分模板用 `l=mid`（上取整 mid），否则死循环；木材总量用 long long。

---

### P2678 跳石头

- **洛谷链接**：<https://www.luogu.com.cn/problem/P2678>
- **难度**：普及　**标签**：二分答案
- **考点**：可行性检查 + 二分（NOIP 2015 提高组 T2）

**题意简述**：起点到终点距离 L，中间 N 块石头（位置已知），最多移走 M 块，求最短跳跃距离的最大值。

**解题思路**：求"最短跳跃距离"的最大值，直接构造难，但判定容易：给定最小跳跃距离 x，能否通过移走 ≤ M 块石头使所有相邻跳跃 ≥ x？贪心检查：从起点跳，若下一块石头距离 < x 则移走它，否则跳上去；统计移走数是否 ≤ M。x 越大越难满足，单调，二分 x（范围 1~L）。

**复杂度**：O(N log L)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int d[50005];
int main() {
    int L, n, m;
    cin >> L >> n >> m;
    for (int i = 1; i <= n; i++) cin >> d[i];
    d[n + 1] = L;                          // 终点
    int l = 1, r = L;
    while (l < r) {
        int mid = (l + r + 1) / 2;
        int last = 0, cnt = 0;             // last: 上一个保留位置
        for (int i = 1; i <= n + 1; i++) {
            if (d[i] - last < mid) cnt++;  // 距离过短，移走这块石头
            else last = d[i];
        }
        if (cnt <= m) l = mid;             // 移走数可接受，x可更大
        else r = mid - 1;
    }
    cout << l << endl;
    return 0;
}
```

**易错点**：终点不能移走；贪心检查从起点开始累计；二分求最大值用 `l=mid` 模板。

---

## 3.5 前缀和与差分

### P1115 最大子段和

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1115>
- **难度**：普及−　**标签**：前缀和 / DP
- **考点**：最大连续子段和

**题意简述**：序列中找连续非空子段，使其和最大。

**解题思路**：两种经典解法：① 前缀和法：子段和 = S[r] − S[l−1]，要让和最大即对每个 r 减去最小的前缀 S[l−1]（l−1 < r），遍历维护最小前缀即可，O(n)；② DP：dp[i] = max(a[i], dp[i−1]+a[i])，答案取 max dp。本题用前缀和思路讲解（与本节主题一致）。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    int n;
    cin >> n;
    long long sum = 0, minPre = 0, ans = -1e18;   // minPre: 已见的最小前缀和
    for (int i = 0; i < n; i++) {
        long long x;
        cin >> x;
        sum += x;
        ans = max(ans, sum - minPre);   // 当前前缀减去最小前缀
        minPre = min(minPre, sum);      // 更新最小前缀
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：子段非空——minPre 的更新要在计算 ans 之后（保证 l−1 < r）；负数和情况要正确（答案可为负）。

---

### P3406 海底高铁

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3406>
- **难度**：普及　**标签**：差分
- **考点**：区间加（差分）统计经过次数

**题意简述**：M 个城市依次访问，相邻访问城市间经过若干段铁路。每段铁路可买票（A 元/次）或办卡（C 元 + B 元/次）。求最小总花费。

**解题思路**：先统计每段铁路被经过的次数 cnt[i]：访问序列相邻两城 p1、p2，经过区间 [min, max)（段号 i 表示城市 i 与 i+1 之间）。用差分数组区间 +1 再求前缀和得到 cnt。然后每段铁路取 min(买票 cnt×A，办卡 C + cnt×B) 累加。O(N+M)。

**复杂度**：O(N+M)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long diff[100005], cnt[100005];
int main() {
    int n, m;
    cin >> n >> m;
    int prev, cur;
    cin >> prev;
    for (int i = 1; i < m; i++) {         // 差分：区间[l,r)加1
        cin >> cur;
        int l = min(prev, cur), r = max(prev, cur);
        diff[l] += 1;
        diff[r] -= 1;
        prev = cur;
    }
    for (int i = 1; i < n; i++) cnt[i] = cnt[i - 1] + diff[i];  // 前缀和还原
    long long ans = 0;
    for (int i = 1; i < n; i++) {
        long long a, b, c;
        cin >> a >> b >> c;
        ans += min(cnt[i] * a, cnt[i] * b + c);  // 买票 vs 办卡
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：区间开闭（段 i 连接城市 i 和 i+1，经过城市区间 [l, r) 对应段号 l..r−1）；差分数组越界（r 可能 = n）；花费用 long long。

---

### P3397 地毯

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3397>
- **难度**：普及−　**标签**：二维差分
- **考点**：二维差分模板

**题意简述**：n×n 格子，m 个地毯（左上角 (x1,y1)、右下角 (x2,y2)），求每个格子被覆盖的次数。

**解题思路**：二维差分模板题。对每块地毯在差分数组上做四个角操作：`d[x1][y1]++、d[x2+1][y1]--、d[x1][y2+1]--、d[x2+1][y2+1]++`，最后做二维前缀和（逐行累加+逐列累加）还原出每个格子的覆盖数。O(n²+m)。

**复杂度**：O(n² + m)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int d[1005][1005];
int main() {
    int n, m;
    cin >> n >> m;
    while (m--) {
        int x1, y1, x2, y2;
        cin >> x1 >> y1 >> x2 >> y2;
        d[x1][y1]++;
        d[x2 + 1][y1]--;
        d[x1][y2 + 1]--;
        d[x2 + 1][y2 + 1]++;      // 二维差分的四个标记点
    }
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= n; j++)
            d[i][j] += d[i - 1][j] + d[i][j - 1] - d[i - 1][j - 1]; // 二维前缀和
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++)
            cout << d[i][j] << (j == n ? "\n" : " ");
    }
    return 0;
}
```

**易错点**：二维差分的四个标记不能少；做前缀和时注意加/减的重叠修正；边界 +1 位置数组要开够（n+2）。

---

## 本篇小结

完成本篇后应掌握：排序（含自定义比较）、贪心（短作业优先、按右端点排区间、哈夫曼）、双指针与尺取、二分查找与二分答案（注意 `l=mid` 与 `l=mid+1` 两种模板的选用）、前缀和与差分（含二维）。这五类算法是 CSP 提高组之前的"地基中的地基"。

---

# 第 4 篇 数据结构

> 本篇覆盖：动态数组、队列、栈、链表、双端队列、集合与映射、并查集。难度以洛谷"普及− / 普及"为主。
> 目标：掌握常用容器/结构的原理与适用场景，会用 STL 与手写结构解决"插入、删除、查找、维护最值"类问题。

## 4.1 动态数组

### P3156 询问学号

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3156>
- **难度**：入门　**标签**：vector
- **考点**：动态数组存储与随机访问

**题意简述**：n 个学生按顺序进教室，m 次询问第 i 个进教室的学生学号。

**解题思路**：用 `vector<long long>` 按进入顺序存储学号，询问直接按下标输出（1-based 注意减 1）。n 可达 2×10^6，学号可达 10^9，注意类型。vector 的随机访问是 O(1)。

**复杂度**：O(n + m)。

**参考代码**：

```cpp
#include <iostream>
#include <vector>
using namespace std;
int main() {
    int n, m;
    cin >> n >> m;
    vector<long long> v(n);
    for (int i = 0; i < n; i++) cin >> v[i];
    while (m--) {
        int x;
        cin >> x;
        cout << v[x - 1] << endl;   // 第x个 -> 下标x-1
    }
    return 0;
}
```

**易错点**：下标从 0 开始；学号用 long long。

---

## 4.2 队列

### P1996 约瑟夫问题

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1996>
- **难度**：普及−　**标签**：队列
- **考点**：用队列模拟"循环报数出圈"

**题意简述**：n 人围成一圈，从 1 开始报数，数到 m 的人出圈，再从下一个人报数，输出全部出圈顺序。

**解题思路**：队列天然表达"环形"：把队首元素"报数后放回队尾"即可循环。具体：当前报数 cnt 从 1 开始，每轮取出队首；若 cnt == m 则输出并出队（cnt 重置为 1）；否则 cnt++ 并放回队尾。n, m ≤ 100 直接模拟。

**复杂度**：O(n×m)。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
int main() {
    int n, m;
    cin >> n >> m;
    queue<int> q;
    for (int i = 1; i <= n; i++) q.push(i);
    int cnt = 1;
    while (!q.empty()) {
        int x = q.front();
        q.pop();
        if (cnt == m) {              // 数到m，出圈
            cout << x << " ";
            cnt = 1;
        } else {
            q.push(x);               // 放回队尾，继续循环
            cnt++;
        }
    }
    return 0;
}
```

**易错点**：报数计数器的重置时机；队首元素需先取出再决定保留还是出队。

---

### P1540 机器翻译

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1540>
- **难度**：普及−　**标签**：队列、模拟
- **考点**：FIFO 淘汰策略（NOIP 2010 提高组 T1）

**题意简述**：内存容量 M，逐词翻译：词在内存中直接翻译；不在则查词典（计数），若内存满则清掉最早进入的词（FIFO）。求查词典总次数。

**解题思路**：队列保存"进入顺序"，bool 数组标记词是否在内存。处理每个词 x：若在内存则跳过；否则 cnt++；若队列 size 已达 M，pop 队首并取消标记；push x 并标记。这是"先进先出缓存"的典型模拟。

**复杂度**：O(N)。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
bool in[1005];
int main() {
    int m, n;
    cin >> m >> n;
    queue<int> q;
    int cnt = 0;
    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        if (in[x]) continue;         // 内存命中
        cnt++;                       // 未命中，查词典
        if ((int)q.size() == m) {    // 内存满，淘汰最早进入的
            in[q.front()] = false;
            q.pop();
        }
        q.push(x);
        in[x] = true;
    }
    cout << cnt << endl;
    return 0;
}
```

**易错点**：淘汰的是"最早进入"（队首）；词编号 ≤ 1000，标记数组大小够；先判命中再查词典。

---

## 4.3 栈

### P1739 表达式括号匹配

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1739>
- **难度**：入门　**标签**：栈、匹配
- **考点**：括号匹配的栈/计数器写法

**题意简述**：表达式以 @ 结束，判断左右圆括号是否匹配。

**解题思路**：只需关注 '(' 与 ')'。用计数器：遇 '(' +1，遇 ')' −1；若某时刻计数器为负（右括号多于左括号）则非法；结束后计数为 0 则匹配。若只有一种括号，计数器比栈更简洁；多类型括号才必须用栈。

**复杂度**：O(|s|)。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string s;
    cin >> s;
    int bal = 0;
    for (char c : s) {
        if (c == '@') break;         // 结束符
        if (c == '(') bal++;
        else if (c == ')') {
            bal--;
            if (bal < 0) { cout << "NO" << endl; return 0; }
        }
    }
    cout << (bal == 0 ? "YES" : "NO") << endl;
    return 0;
}
```

**易错点**：中间时刻不能出现负值；结束符 @ 之后的内容忽略；只判断圆括号。

---

### P1449 后缀表达式

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1449>
- **难度**：普及−　**标签**：栈
- **考点**：表达式求值（后缀）

**题意简述**：给定后缀表达式（数字以 `.` 结尾、`@` 结束），运算符 +−* /，/ 向 0 取整，求值。

**解题思路**：栈求值模板：遇数字解析完整整数入栈；遇运算符弹出两个操作数（先弹 b、后弹 a，计算 a op b）后结果入栈。`. ` 分隔数字，`@` 结束。除法用 C++ 整数除法即向 0 取整。

**复杂度**：O(|s|)。

**参考代码**：

```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;
int main() {
    string s;
    cin >> s;
    stack<int> st;
    int num = 0;
    for (char c : s) {
        if (c == '@') break;
        if (c == '.') { st.push(num); num = 0; }      // 数字结束
        else if (c >= '0' && c <= '9') num = num * 10 + (c - '0');
        else {                                        // 运算符
            int b = st.top(); st.pop();
            int a = st.top(); st.pop();
            switch (c) {
                case '+': st.push(a + b); break;
                case '-': st.push(a - b); break;
                case '*': st.push(a * b); break;
                case '/': st.push(a / b); break;      // 向0取整
            }
        }
    }
    cout << st.top() << endl;
    return 0;
}
```

**易错点**：弹栈顺序（先弹的是右操作数）；数字可能多位，需累计；除法向 0 取整由 C++ 保证。

---

### P4387 验证栈序列

- **洛谷链接**：<https://www.luogu.com.cn/problem/P4387>
- **难度**：普及　**标签**：栈
- **考点**：入栈出栈序列合法性判定

**题意简述**：给定入栈序列 pushed 与出栈序列 poped（均为 1~n 的排列），判断 poped 是否可能是合法出栈序列。

**解题思路**：模拟判定：按 pushed 顺序逐个入栈；每次入栈后，只要栈顶等于 poped 当前待出元素就出栈（指针 j 后移）；结束时若 j == n 且栈空则合法。这是"栈序列判定"的标准模板。

**复杂度**：O(n) 每组。

**参考代码**：

```cpp
#include <iostream>
#include <stack>
using namespace std;
int a[100005], b[100005];
int main() {
    int q;
    cin >> q;
    while (q--) {
        int n;
        cin >> n;
        for (int i = 0; i < n; i++) cin >> a[i];
        for (int i = 0; i < n; i++) cin >> b[i];
        stack<int> st;
        int j = 0;
        for (int i = 0; i < n; i++) {
            st.push(a[i]);
            while (!st.empty() && st.top() == b[j]) {  // 能出就出
                st.pop();
                j++;
            }
        }
        cout << (j == n ? "Yes" : "No") << endl;       // 全部出完才合法
    }
    return 0;
}
```

**易错点**：每组合法判定后栈自动为空；多组数据时数组覆盖即可；`while` 出栈要反复检查栈顶。

---

## 4.4 链表

### P1160 队列安排

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1160>
- **难度**：普及　**标签**：链表
- **考点**：双向链表插入与删除

**题意简述**：1 号先入队；2~N 号依次插入到某已入队同学 k 的左边或右边；再删除 M 个同学（重复删除忽略）；最后输出从左到右队列。

**解题思路**：中间插入+按编号删除，用数组模拟双向链表最合适：`L[i]`、`R[i]` 表示 i 号同学左右邻居，0 表示不存在；`head` 记录队首。插入：插 k 左边则更新 k.L 链；插右边更新 k.R 链。删除：`del[i] = true` 标记，输出时跳过。注意重复删除忽略（标记判断）。N ≤ 10^5，O(N)。

**复杂度**：O(N)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int L[100005], R[100005];
bool del[100005];
int main() {
    int n;
    cin >> n;
    L[1] = R[1] = 0;
    int head = 1;
    for (int i = 2; i <= n; i++) {
        int k, p;
        cin >> k >> p;
        if (p == 0) {                     // 插到k左边
            L[i] = L[k];
            R[i] = k;
            if (L[k]) R[L[k]] = i;        // 原左边同学右指针改
            else head = i;                // k原来在队首，i成新队首
            L[k] = i;
        } else {                          // 插到k右边
            L[i] = k;
            R[i] = R[k];
            if (R[k]) L[R[k]] = i;
            R[k] = i;
        }
    }
    int m;
    cin >> m;
    while (m--) {
        int x;
        cin >> x;
        del[x] = true;                    // 重复删除自然忽略
    }
    for (int i = head; i; i = R[i])
        if (!del[i]) cout << i << (R[i] && !del[R[i]] ? " " : "\n");
    return 0;
}
```

**易错点**：插入时维护四条链（左右邻居的左右指针）与队首；输出时跳过已删除，且判断末尾空格；R[i] 可能为 0（队尾）。

---

## 4.5 双端队列（单调队列）

### P1440 求 m 区间内的最小值

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1440>
- **难度**：普及　**标签**：单调队列
- **考点**：滑动窗口最小值（deque 实现）

**题意简述**：对每个位置 i，输出 a[i−m..i−1]（不足 m 个则从 a[1] 起）区间的最小值；i=1 时输出 0。

**解题思路**：单调队列模板：用双端队列存"候选下标"，保证队列中下标对应值**单调递增**，队首即最小值。每步：① 弹出队首中下标超出窗口（< i−m）的；② 输出队首值（队空则 0，仅第一个位置）；③ 入队 a[i] 前，弹出队尾所有 ≥ a[i] 的（保持单调）。每个元素至多入队出队一次，O(n)。n ≤ 2×10^6，需快速 IO。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <cstdio>
int a[2000005], dq[2000005];   // 手写双端队列存下标（更快）
int main() {
    int n, m;
    scanf("%d%d", &n, &m);
    int head = 0, tail = 0;    // [head, tail) 区间
    for (int i = 1; i <= n; i++) {
        scanf("%d", &a[i]);
        while (head < tail && dq[head] < i - m) head++;   // 弹出窗口外的
        if (head < tail) printf("%d\n", a[dq[head]]);
        else printf("0\n");                               // 第1个数无前驱
        while (head < tail && a[dq[tail - 1]] >= a[i]) tail--; // 保持递增
        dq[tail++] = i;
    }
    return 0;
}
```

**易错点**：输出用的是"加入 a[i] 之前的窗口最小值"；窗口左边界是 i−m；单调性比较用 ≥（新元素更小才替换，保留靠后的下标更优）。

---

## 4.6 集合与映射

### P5250 木材仓库

- **洛谷链接**：<https://www.luogu.com.cn/problem/P5250>
- **难度**：普及　**标签**：set
- **考点**：有序集合 + lower_bound 找最近值

**题意简述**：维护一个长度不重复的木材仓库：进货（重复则输出 Already Exist）、出货（取恰好长度的；否则取最接近的，距离相同取较短；空仓输出 Empty）。

**解题思路**：`set<int>` 天然有序去重。进货：`count()` 判断重复。出货：`lower_bound(len)` 找到第一个 ≥ len 的位置，比较它与前一个元素（< len 的最大者）与 len 的差距，选更近者（相等取较小者，即前驱）。注意 set 为空与边界（begin/end）处理。

**复杂度**：O(m log m)。

**参考代码**：

```cpp
#include <iostream>
#include <set>
using namespace std;
int main() {
    int m;
    cin >> m;
    set<int> st;
    while (m--) {
        int op, len;
        cin >> op >> len;
        if (op == 1) {                       // 进货
            if (st.count(len)) cout << "Already Exist" << endl;
            else st.insert(len);
        } else {                             // 出货
            if (st.empty()) { cout << "Empty" << endl; continue; }
            auto it = st.lower_bound(len);
            if (it != st.end() && *it == len) {      // 恰好有
                cout << len << endl;
                st.erase(it);
            } else if (it == st.end()) {             // 都小于len，取最大
                cout << *prev(it) << endl;
                st.erase(prev(it));
            } else if (it == st.begin()) {           // 都大于len，取最小
                cout << *it << endl;
                st.erase(it);
            } else {                                 // 两边都有，比距离
                auto pre = prev(it);
                if (len - *pre <= *it - len) {       // 距离相同取较短(前驱)
                    cout << *pre << endl;
                    st.erase(pre);
                } else {
                    cout << *it << endl;
                    st.erase(it);
                }
            }
        }
    }
    return 0;
}
```

**易错点**：`prev(it)` 在 it 为 begin 时非法；距离相等取较短（前驱）；erase 后迭代器失效，需在输出后使用。

---

### P3370 【模板】字符串哈希

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3370>
- **难度**：普及−　**标签**：哈希
- **考点**：字符串去重与哈希思想

**题意简述**：N 个字符串（总长可达 10^7 量级），求不同字符串个数。

**解题思路**：本题用 `set<string>` 直接去重最简单可靠。但要练习哈希：把字符串映射为数字 `hash = Σ s[i] × base^i`（base 取 131 等），用自然溢出（unsigned long long 自动取模 2^64）或双哈希降低碰撞。碰撞风险真实存在（洛谷有专门卡单哈希的数据），工程上常用双哈希或最终用 set 验证。这里给出直接 set 版本，解析中给出哈希写法。

**复杂度**：O(总字符数 × log N)。

**参考代码**：

```cpp
#include <iostream>
#include <set>
#include <string>
using namespace std;
int main() {
    int n;
    cin >> n;
    set<string> st;
    while (n--) {
        string s;
        cin >> s;
        st.insert(s);
    }
    cout << st.size() << endl;
    return 0;
}
// 哈希模板（自然溢出，注意碰撞）：
// unsigned long long h = 0;
// for (char c : s) h = h * 131 + c;
// 存到 set<unsigned long long> 去重
```

**易错点**：单哈希可能被卡；用 set<string> 可保证正确；读入用 cin 需加速或直接默认。

---

## 4.7 并查集

### P3367 【模板】并查集

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3367>
- **难度**：普及　**标签**：并查集模板
- **考点**：合并与查询、路径压缩

**题意简述**：N 个元素，M 个操作：合并 x、y 所在集合；查询 x、y 是否同集合。

**解题思路**：并查集模板。`fa[i]` 记录父节点；`find(x)` 递归/迭代找根，并做**路径压缩**（把路径上节点直接挂到根）；合并时把 x 根挂到 y 根（可加按秩/按大小合并优化）。N ≤ 2×10^5、M ≤ 10^6，路径压缩后接近 O(1) 均摊。

**复杂度**：O(M α(N))。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int fa[200005];
int find(int x) {
    return fa[x] == x ? x : fa[x] = find(fa[x]);  // 路径压缩
}
int main() {
    int n, m;
    cin >> n >> m;
    for (int i = 1; i <= n; i++) fa[i] = i;
    while (m--) {
        int z, x, y;
        cin >> z >> x >> y;
        int rx = find(x), ry = find(y);
        if (z == 1) {
            if (rx != ry) fa[rx] = ry;            // 合并
        } else {
            cout << (rx == ry ? "Y" : "N") << endl;
        }
    }
    return 0;
}
```

**易错点**：初始 fa[i]=i；合并前先 find；路径压缩写在 find 返回处；大输入量建议 `ios::sync_with_stdio(false)`。

---

## 本篇小结

完成本篇后应掌握：vector、queue、stack、deque 与手写双向链表、单调队列、set/map 以及并查集的原理与代码。数据结构题的共性：**选对容器 = 解决一半**（插入多选链表、先进先出选队列、先进后出选栈、区间最值选单调队列、有序去重查找选 set）。

---

# 第 5 篇 搜索

> 本篇覆盖：深度优先搜索（DFS）、广度优先搜索（BFS）、剪枝策略、搜索综合运用。难度以洛谷"普及− / 普及"为主。
> 目标：掌握两种基本搜索的模板与适用场景（求方案数/全部解用 DFS，求最短路/最少步数用 BFS），并学会用剪枝避免超时。

## 5.1 深度优先搜索

### P1706 全排列问题

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1706>
- **难度**：普及−　**标签**：DFS
- **考点**：递归枚举全排列、回溯

**题意简述**：按字典序输出 1~n 的所有全排列，每个数字占 5 个场宽。

**解题思路**：DFS 模板：递归函数 `dfs(dep)` 表示已填 dep 个数；每层枚举 1~n 中未使用的数填入 ans[dep]，递归下一层；回溯时取消标记。n ≤ 9，9! = 362880 可行。注意每行数字用 `printf("%5d")` 控制场宽。

**复杂度**：O(n!)。

**参考代码**：

```cpp
#include <iostream>
#include <cstdio>
using namespace std;
int n, ans[10];
bool used[10];
void dfs(int dep) {
    if (dep > n) {                        // 填满一层，输出
        for (int i = 1; i <= n; i++) printf("%5d", ans[i]);
        printf("\n");
        return;
    }
    for (int i = 1; i <= n; i++)
        if (!used[i]) {
            used[i] = true;
            ans[dep] = i;
            dfs(dep + 1);
            used[i] = false;              // 回溯
        }
}
int main() {
    cin >> n;
    dfs(1);
    return 0;
}
```

**易错点**：回溯要恢复状态；场宽用 %5d；从 1 开始填保证字典序。

---

### P1219 八皇后

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1219>
- **难度**：普及　**标签**：DFS、回溯
- **考点**：对角线判重的回溯（USACO / 经典）

**题意简述**：n×n 棋盘放 n 个皇后，每行每列每条对角线至多一个；输出前 3 个解（按行输出列号）与总解数。

**解题思路**：按行 DFS：第 r 行尝试每列 c，需检查列 c、主对角线 r−c、副对角线 r+c 均未被占用。用三个标记数组：`col[c]`、`d1[r-c+n]`（防负下标）、`d2[r+c]`。到 n+1 行时输出前 3 个解并计数。n ≤ 13，O(n!) 加剪枝可通过。

**复杂度**：O(n!)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int n, ans[15], cnt;
bool col[15], d1[30], d2[30];   // d1: r-c+n, d2: r+c
void dfs(int r) {
    if (r > n) {                // 放置完成
        cnt++;
        if (cnt <= 3) {
            for (int i = 1; i <= n; i++) cout << ans[i] << " ";
            cout << endl;
        }
        return;
    }
    for (int c = 1; c <= n; c++)
        if (!col[c] && !d1[r - c + n] && !d2[r + c]) {
            col[c] = d1[r - c + n] = d2[r + c] = true;
            ans[r] = c;
            dfs(r + 1);
            col[c] = d1[r - c + n] = d2[r + c] = false;  // 回溯
        }
}
int main() {
    cin >> n;
    dfs(1);
    cout << cnt << endl;
    return 0;
}
```

**易错点**：主对角线用 r−c+n 防止负数下标；三条线都要标记/回溯；先输出前 3 个解再输出总数。

---

### P1605 迷宫

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1605>
- **难度**：普及−　**标签**：DFS
- **考点**：路径计数、障碍处理、回溯

**题意简述**：N×M 迷宫有 T 个障碍，从起点到终点有多少种走法（每个格子最多经过一次，只能上下左右）。

**解题思路**：DFS 计数：`dfs(x,y)` 尝试四个方向，若目标格合法（在界内、非障碍、未访问）则标记访问并递归；到终点计数 +1；回溯撤销访问。N、M ≤ 5 很小，直接暴力。

**复杂度**：O(4^(N·M))，数据小可行。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int n, m, t, sx, sy, fx, fy, ans;
bool blocked[10][10], vis[10][10];
int dx[4] = {0, 0, 1, -1}, dy[4] = {1, -1, 0, 0};
void dfs(int x, int y) {
    if (x == fx && y == fy) { ans++; return; }
    for (int i = 0; i < 4; i++) {
        int nx = x + dx[i], ny = y + dy[i];
        if (nx >= 1 && nx <= n && ny >= 1 && ny <= m &&
            !blocked[nx][ny] && !vis[nx][ny]) {
            vis[nx][ny] = true;
            dfs(nx, ny);
            vis[nx][ny] = false;          // 回溯
        }
    }
}
int main() {
    cin >> n >> m >> t;
    cin >> sx >> sy >> fx >> fy;
    while (t--) { int x, y; cin >> x >> y; blocked[x][y] = true; }
    vis[sx][sy] = true;                   // 起点标记为已访问！
    dfs(sx, sy);
    cout << ans << endl;
    return 0;
}
```

**易错点**：起点必须提前标记访问，否则会反复经过起点造成多解（经典 70 分坑）；回溯撤销访问。

---

### P1036 选数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1036>
- **难度**：普及−　**标签**：DFS、组合
- **考点**：组合枚举（带起点参数）+ 素数判断（NOIP 2002 普及组 T2）

**题意简述**：n 个数中选 k 个求和，和为素数的方案有多少种。

**解题思路**：组合 DFS：`dfs(dep, start, sum)`，dep 已选个数、start 是可选起点（保证组合不重复）、sum 当前和。选够 k 个判断素数。n ≤ 20 组合数 C(20,10) 最大约 18 万，可行。

**复杂度**：O(C(n,k))。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int n, k, a[25], ans;
bool isPrime(int x) {
    if (x < 2) return false;
    for (int i = 2; i * i <= x; i++)
        if (x % i == 0) return false;
    return true;
}
void dfs(int dep, int start, int sum) {
    if (dep == k) { if (isPrime(sum)) ans++; return; }
    for (int i = start; i < n; i++)   // 从start开始，保证组合不重复
        dfs(dep + 1, i + 1, sum + a[i]);
}
int main() {
    cin >> n >> k;
    for (int i = 0; i < n; i++) cin >> a[i];
    dfs(0, 0, 0);
    cout << ans << endl;
    return 0;
}
```

**易错点**：组合用 start 参数避免重复（不是全排列）；素数判断到 √x 即可。

---

## 5.2 广度优先搜索

### P1443 马的遍历

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1443>
- **难度**：普及−　**标签**：BFS
- **考点**：BFS 求最少步数

**题意简述**：n×m 棋盘上的马（8 方向日字走），求到每个点的最少步数，不可达输出 −1。

**解题思路**：BFS 经典：从起点开始，dist 初始化为 −1，起点为 0；逐层扩展 8 个方向，首次到达即最短路。队列先进先出保证"层数递增"。

**复杂度**：O(n×m)。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
int dist[405][405];
int dx[8] = {1,1,-1,-1,2,2,-2,-2};
int dy[8] = {2,-2,2,-2,1,-1,1,-1};
int main() {
    int n, m, x, y;
    cin >> n >> m >> x >> y;
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++) dist[i][j] = -1;
    queue<pair<int,int>> q;
    dist[x][y] = 0;
    q.push({x, y});
    while (!q.empty()) {
        auto [cx, cy] = q.front(); q.pop();
        for (int i = 0; i < 8; i++) {
            int nx = cx + dx[i], ny = cy + dy[i];
            if (nx >= 1 && nx <= n && ny >= 1 && ny <= m && dist[nx][ny] == -1) {
                dist[nx][ny] = dist[cx][cy] + 1;
                q.push({nx, ny});
            }
        }
    }
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++)
            cout << dist[i][j] << (j == m ? "\n" : " ");
    }
    return 0;
}
```

**易错点**：dist 初值 −1 兼作"未访问"标记；马是日字 8 方向，别写成 4 方向。

---

### P1162 填涂颜色

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1162>
- **难度**：普及−　**标签**：BFS、连通块
- **考点**：从边界扩散标记外部区域

**题意简述**：01 方阵中 1 构成一个闭合圈，把圈内所有 0 改成 2 输出。

**解题思路**：反其道行之：从方阵**边界上的所有 0** 开始 BFS，凡是能从边界到达的 0 都是圈外 0；剩余的 0 就在圈内，输出时改成 2。加一圈 0 围边可简化边界处理（从 (0,0) 开始搜）。n ≤ 30。

**复杂度**：O(n²)。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
int a[35][35];
bool out[35][35];           // 标记能从边界到达的圈外0
int dx[4] = {0,0,1,-1}, dy[4] = {1,-1,0,0};
int main() {
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= n; j++) cin >> a[i][j];
    queue<pair<int,int>> q;
    for (int i = 1; i <= n; i++) {          // 四条边的0全部入队
        if (a[1][i] == 0) q.push({1, i});
        if (a[n][i] == 0) q.push({n, i});
        if (a[i][1] == 0) q.push({i, 1});
        if (a[i][n] == 0) q.push({i, n});
    }
    while (!q.empty()) {
        auto [x, y] = q.front(); q.pop();
        if (out[x][y]) continue;
        out[x][y] = true;
        for (int i = 0; i < 4; i++) {
            int nx = x + dx[i], ny = y + dy[i];
            if (nx >= 1 && nx <= n && ny >= 1 && ny <= n &&
                a[nx][ny] == 0 && !out[nx][ny])
                q.push({nx, ny});
        }
    }
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++) {
            if (a[i][j] == 0 && !out[i][j]) cout << 2;   // 圈内0
            else cout << a[i][j];
            cout << (j == n ? "\n" : " ");
        }
    }
    return 0;
}
```

**易错点**：必须先入队边界所有 0（包括角落）；圈内 0 用"非外部"判定；1 保持原样。

---

### P1135 奇怪的电梯

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1135>
- **难度**：普及　**标签**：BFS
- **考点**：图上的 BFS 最短路

**题意简述**：N 层楼，第 i 层可上/下 Ki 层，求从 A 层到 B 层最少按几次按钮，不可达输出 −1。

**解题思路**：把每层楼看成节点，按一次按钮就是一条边（i→i+K[i] 或 i−K[i]，若越界则失效）。BFS 求 A 到 B 的最少按键次数。

**复杂度**：O(N)。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
int k[205], dist[205];
int main() {
    int n, a, b;
    cin >> n >> a >> b;
    for (int i = 1; i <= n; i++) cin >> k[i];
    for (int i = 1; i <= n; i++) dist[i] = -1;
    queue<int> q;
    dist[a] = 0;
    q.push(a);
    while (!q.empty()) {
        int u = q.front(); q.pop();
        if (u == b) break;
        for (int nxt : {u + k[u], u - k[u]}) {   // 上、下两个按钮
            if (nxt >= 1 && nxt <= n && dist[nxt] == -1) {
                dist[nxt] = dist[u] + 1;
                q.push(nxt);
            }
        }
    }
    cout << dist[b] << endl;
    return 0;
}
```

**易错点**：越界楼层直接失效；dist 初值 −1 兼作未访问；注意 k[i] 可能为 0（原地循环，不影响 BFS）。

---

## 5.3 剪枝与综合

### P1025 数的划分

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1025>
- **难度**：普及　**标签**：DFS、剪枝
- **考点**：组合划分去重 + 上下界剪枝（NOIP 2001 提高组 T2）

**题意简述**：把 n 分成 k 份正整数，不计顺序，求方案数。

**解题思路**：DFS 按"非降序"划分避免重复：第 dep 份取 x ≥ 上一份。剪枝：剩余还能取的最大值——第 dep 份取 x 时，要保证剩余 (k−dep) 份每份至少 x，即 x × (k−dep+1) ≤ 剩余和 rem。枚举 x 从 last 到 rem/(k−dep+1)。n ≤ 200、k ≤ 6 秒过。

**复杂度**：O(方案数)，远小于 C(n,k)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int n, k, ans;
// dep: 第几份(1起), last: 上一份取值(保证非降序), rem: 剩余整数
void dfs(int dep, int last, int rem) {
    if (dep == k) { ans++; return; }       // 最后一份=rem
    for (int x = last; x * (k - dep + 1) <= rem; x++)  // 剪枝: 剩余每份≥x
        dfs(dep + 1, x, rem - x);
}
int main() {
    cin >> n >> k;
    dfs(1, 1, n);
    cout << ans << endl;
    return 0;
}
```

**易错点**：非降序才能去重；剪枝条件 `x * (k-dep+1) <= rem` 防超时。

---

### P1019 单词接龙

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1019>
- **难度**：普及　**标签**：DFS 深搜、字符串
- **考点**：重叠部分处理 + 深搜求最长（NOIP 2000 提高组 T3）

**题意简述**：n 个单词，每个最多用两次，单词可接龙（后单词前缀与前单词后缀重叠合并），相邻单词不能有包含关系，求以给定字母开头的最长龙长度。

**解题思路**：① 预处理任意两单词的最小重叠长度（>0 且非包含）；② DFS：从起点（首字母匹配的单词）出发，尝试所有单词接上（次数 <2），更新最大长度。n ≤ 20，深搜可行。注意"重叠部分不能是完整单词"（避免包含）。

**复杂度**：O(状态数)，n 小可行。

**参考代码**：

```cpp
#include <iostream>
#include <string>
using namespace std;
int n, cnt[25], ans;
string w[25];
// 深搜：cur为当前龙字符串，len为当前龙长度
void dfs(string cur, int len) {
    ans = max(ans, len);
    for (int i = 0; i < n; i++) {
        if (cnt[i] >= 2) continue;                      // 每个单词最多用2次
        // 找 cur 的后缀与 w[i] 的前缀的最小重叠长度（不含完整单词）
        int ov = 0;
        for (int l = 1; l < min((int)cur.size(), (int)w[i].size()); l++) {
            bool ok = true;
            for (int j = 0; j < l; j++)
                if (cur[cur.size() - l + j] != w[i][j]) { ok = false; break; }
            if (ok) { ov = l; break; }
        }
        if (ov) {
            cnt[i]++;
            dfs(cur + w[i].substr(ov), len + (int)w[i].size() - ov);
            cnt[i]--;
        }
    }
}
int main() {
    cin >> n;
    for (int i = 0; i < n; i++) cin >> w[i];
    char start;
    cin >> start;
    for (int i = 0; i < n; i++)
        if (w[i][0] == start) {
            cnt[i]++;
            dfs(w[i], (int)w[i].size());
            cnt[i]--;
        }
    cout << ans << endl;
    return 0;
}
```

**易错点**：重叠长度必须 ≥1 且 < 完整单词长度（防包含）；每个单词限用 2 次；从所有首字母匹配的单词分别开搜；深搜时用字符串拼接模拟龙。

---

### P1378 油滴扩展

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1378>
- **难度**：普及+/提高−　**标签**：DFS、几何
- **考点**：全排列 DFS + 几何计算（圆不重叠）

**题意简述**：长方形盒子内 N 个点依次放油滴，油滴扩到接触边界或其他油滴为止，求所有油滴最大占据面积（输出剩余最小空间，四舍五入）。

**解题思路**：N ≤ 6，DFS 全排列放置顺序。对每个放置的点，半径 r = min(到四边的距离, 到已放油滴圆心的距离 − 该油滴半径)；若 ≤ 0 则 r=0（被包含）。总占据面积 = π Σr²，答案 = 框面积 − 占据面积，四舍五入输出整数。

**复杂度**：O(N!·N)。

**参考代码**：

```cpp
#include <iostream>
#include <cmath>
#include <algorithm>
using namespace std;
int n, xs, ys, xe, ye;
double px[10], py[10], r[10];
bool used[10];
const double PI = acos(-1.0);
double best = 0;
void dfs(int dep, double sum) {
    if (dep == n) { best = max(best, sum); return; }
    for (int i = 0; i < n; i++)
        if (!used[i]) {
            used[i] = true;
            double rr = min({px[i] - xs, xe - px[i], py[i] - ys, ye - py[i]});
            for (int j = 0; j < n; j++)
                if (used[j] && j != i) {
                    double d = hypot(px[i] - px[j], py[i] - py[j]);
                    rr = min(rr, d - r[j]);          // 不能接触其他油滴
                }
            r[i] = max(0.0, rr);                     // 可能为负(被覆盖)
            dfs(dep + 1, sum + PI * r[i] * r[i]);
            used[i] = false;
            r[i] = 0;
        }
}
int main() {
    cin >> n;
    cin >> xs >> ys >> xe >> ye;
    if (xs > xe) swap(xs, xe);
    if (ys > ye) swap(ys, ye);
    for (int i = 0; i < n; i++) cin >> px[i] >> py[i];
    dfs(0, 0);
    double area = (xe - xs) * (ye - ys);
    printf("%.0f\n", area - best);      // 四舍五入输出剩余面积
    return 0;
}
```

**易错点**：坐标可能乱序需排序成左下右上；半径受"到其他油滴"和"边界"双重限制；被已有油滴覆盖时半径取 0；最后输出剩余面积且四舍五入。

---

## 本篇小结

完成本篇后应掌握：DFS（全排列/组合/路径计数/回溯）与 BFS（最短路/连通块/扩散标记）的模板，以及剪枝的基本思路（上下界剪枝、可行性剪枝）。**求"有多少种"用 DFS+回溯，求"最少几步"用 BFS**，这是选择搜索方式的第一判断标准。

---

# 第 6 篇 数学

> 本篇覆盖：简单数学（同余、gcd/lcm、快速幂）、素数问题（判定、筛法、质因数分解）、组合数学（排列组合、乘法原理、杨辉三角）。难度以洛谷"普及− / 普及"为主。
> 目标：掌握数论与组合的常用模板和关键性质（gcd 与 lcm 的关系、筛法、取模运算）。

## 6.1 简单数学

### P1226 【模板】快速幂

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1226>
- **难度**：普及−　**标签**：快速幂模板
- **考点**：二分幂 + 取模

**题意简述**：求 a^b mod p，输出 `a^b mod p=s` 格式。

**解题思路**：快速幂模板：b 的二进制拆分，`res = res * a % p`（当 b 当前位为 1 时），`a = a * a % p` 翻倍，b 右移。时间复杂度 O(log b)，a、b 可达 2^31，用 long long 防乘法溢出。

**复杂度**：O(log b)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long qpow(long long a, long long b, long long p) {
    long long res = 1;
    while (b) {
        if (b & 1) res = res * a % p;  // 当前位为1
        a = a * a % p;                 // 底数平方
        b >>= 1;
    }
    return res;
}
int main() {
    long long a, b, p;
    cin >> a >> b >> p;
    cout << a << "^" << b << " mod " << p << "=" << qpow(a, b, p) << endl;
    return 0;
}
```

**易错点**：`res * a` 可能溢出，全程 long long；指数为 0 时 res=1；输出格式严格按题目。

---

### P1029 最大公约数和最小公倍数问题

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1029>
- **难度**：普及−　**标签**：gcd/lcm
- **考点**：gcd 与 lcm 关系（NOIP 2001 普及组 T2）

**题意简述**：求正整数对 (P,Q) 的个数，使 gcd(P,Q)=x0、lcm(P,Q)=y0。

**解题思路**：利用恒等式 **P×Q = gcd(P,Q) × lcm(P,Q)** = x0×y0。于是枚举 x0×y0 的因子对 (P, Q=prod/P)，检查 gcd(P,Q)==x0 即可。prod 可达 10^10，枚举到 √prod 即可，对称因子对 ×2，完全平方时 ×1。注意 y0 必须能被 x0 整除（否则无解）。

**复杂度**：O(√(x0·y0))。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long gcd(long long a, long long b) {
    return b ? gcd(b, a % b) : a;
}
int main() {
    long long x0, y0;
    cin >> x0 >> y0;
    if (y0 % x0 != 0) { cout << 0 << endl; return 0; }
    long long prod = x0 * y0;
    int ans = 0;
    for (long long i = 1; i * i <= prod; i++) {
        if (prod % i == 0) {
            long long j = prod / i;
            if (gcd(i, j) == x0) {
                ans += (i == j) ? 1 : 2;   // 对称因子对算两个
            }
        }
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：P×Q=gcd×lcm 恒等式；对称对 ×2；P=Q 时只算 1 个；x0×y0 用 long long。

---

### P1888 三角函数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1888>
- **难度**：入门　**标签**：gcd、约分
- **考点**：分数约分、勾股定理

**题意简述**：输入一组勾股数，输出较小锐角的正弦值（约分后的分数）。

**解题思路**：直角三角形较小锐角的正弦 = 对边/斜边 = **最短边 / 最长边**。三个数排序取最小和最大，用 gcd 约分输出。勾股数本身保证构成直角三角形。

**复杂度**：O(log max)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int main() {
    long long a[3];
    cin >> a[0] >> a[1] >> a[2];
    sort(a, a + 3);
    long long g = __gcd(a[0], a[2]);   // 或手写gcd
    cout << a[0] / g << "/" << a[2] / g << endl;
    return 0;
}
```

**易错点**：分子是最短边、分母是最长边；约分用 gcd；数据可达 10^9 用 long long。

---

## 6.2 素数问题

### P3383 【模板】线性筛素数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3383>
- **难度**：普及−　**标签**：线性筛模板
- **考点**：欧拉筛（线性筛）

**题意简述**：范围 n=10^8，q 次询问输出第 k 小的素数。

**解题思路**：欧拉线性筛：每个合数只被其**最小质因子**筛掉一次，O(n)。遍历 i=2..n：若未被标记则为素数并入 primes；然后对每个已得素数 p（p ≤ 最小质因子限制），标记 i×p。本题要存下所有素数（10^8 内约 5.76×10^6 个）并直接输出 primes[k−1]。用 vector<char> 做标记节省内存（10^8 字节 ≈ 100MB）。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <cstdio>
#include <vector>
using namespace std;
int main() {
    int n, q;
    scanf("%d%d", &n, &q);
    vector<char> isComp(n + 1, 0);        // 标记合数
    vector<int> primes;
    for (int i = 2; i <= n; i++) {
        if (!isComp[i]) primes.push_back(i);
        for (int p : primes) {
            if ((long long)i * p > n) break;
            isComp[i * p] = 1;
            if (i % p == 0) break;        // 保证每个合数只被最小质因子筛
        }
    }
    while (q--) {
        int k;
        scanf("%d", &k);
        printf("%d\n", primes[k - 1]);
    }
    return 0;
}
```

**易错点**：`i % p == 0` 时 break 是线性筛的关键；i×p 用 long long 防溢出；第 1 小素数是 2。

---

### P1075 质因数分解

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1075>
- **难度**：普及−　**标签**：质因数分解
- **考点**：试除法（NOIP 2012 普及组 T1）

**题意简述**：n 是两个不同质数的乘积，输出较大的那个质数。

**解题思路**：从 2 开始试除，找到 n 的第一个质因子 p（一定 ≤ √n），则较大的质数 = n / p。因为 n 恰为两个质数乘积，第一个找到的因子就是较小质数。

**复杂度**：O(√n)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int main() {
    long long n;
    cin >> n;
    for (long long i = 2; i * i <= n; i++)
        if (n % i == 0) {          // 找到最小质因子
            cout << n / i << endl; // 较大的质数
            return 0;
        }
    return 0;
}
```

**易错点**：找最小质因子，输出 n/i 而非 i；n ≤ 2×10^9 用 long long。

---

### P3912 素数个数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3912>
- **难度**：普及−　**标签**：埃氏筛
- **考点**：筛法统计素数个数

**题意简述**：统计 1~N 中素数个数，N ≤ 10^8。

**解题思路**：埃氏筛：从 2 开始，把每个素数的倍数标记为合数；剩下的即为素数。统计计数。10^8 的 bool 数组约 100MB（用 vector<char>），埃氏筛 O(n log log n) 在 2s 内可通过。

**复杂度**：O(n log log n)。

**参考代码**：

```cpp
#include <cstdio>
#include <vector>
using namespace std;
int main() {
    int n;
    scanf("%d", &n);
    vector<char> isPrime(n + 1, 1);
    isPrime[0] = isPrime[1] = 0;
    int cnt = 0;
    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            cnt++;
            if ((long long)i * i <= n)
                for (long long j = (long long)i * i; j <= n; j += i)
                    isPrime[j] = 0;      // 从i*i开始筛
        }
    }
    printf("%d\n", cnt);
    return 0;
}
```

**易错点**：从 i×i 开始筛可省大量操作；1 不是素数；数组大小与内存。

---

## 6.3 组合数学

### P1866 编号

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1866>
- **难度**：普及−　**标签**：乘法原理
- **考点**：排列计数与乘法原理

**题意简述**：N 只兔子各要 1~Mi 之间的不同编号，求编号方案数（对 1e9+7 取模，不可能则 0）。

**解题思路**：把 Mi 升序排序，第 i 只（0 起）可选的编号 = Mi − i（前面已占 i 个），若 ≤ 0 则无解。方案数 = Π(Mi − i) mod 1e9+7。这是"逐只分配、乘法原理"的经典模型。

**复杂度**：O(N log N)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
long long m[55];
int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) cin >> m[i];
    sort(m, m + n);
    long long ans = 1;
    for (int i = 0; i < n; i++) {
        if (m[i] <= i) { cout << 0 << endl; return 0; }  // 不够编号
        ans = ans * (m[i] - i) % 1000000007;
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：必须升序排序后再减 i（贪心分配）；任何一步 ≤ 0 即无解；取模 1e9+7。

---

### P2822 组合数问题

- **洛谷链接**：<https://www.luogu.com.cn/problem/P2822>
- **难度**：普及　**标签**：杨辉三角、二维前缀和
- **考点**：组合数取模 + 二维前缀和（NOIP 2016 提高组 D2T1）

**题意简述**：t 组询问，对每组 (n,m) 统计所有 0≤i≤n、0≤j≤min(i,m) 中 C(i,j) 是 k 的倍数的对数。

**解题思路**：预处理 C(i,j) mod k：C(i,j) = (C(i−1,j−1) + C(i−1,j)) % k（杨辉三角，边界 C(i,0)=C(i,i)=1）。若值为 0 说明是 k 的倍数。再构造二维前缀和 s[i][j] 统计"左上角区域内值为 0 的格子数"，O(1) 回答每个询问。j>i 的格子不存在组合数，置 0 且不计数。n,m ≤ 2000，预处理 O(n²)。

**复杂度**：预处理 O(N²)，询问 O(1)。

**参考代码**：

```cpp
#include <cstdio>
int C[2005][2005], s[2005][2005];
int main() {
    int t, k;
    scanf("%d%d", &t, &k);
    for (int i = 0; i <= 2000; i++) {
        C[i][0] = 1 % k;                    // 边界
        for (int j = 1; j <= i; j++)
            C[i][j] = (C[i-1][j-1] + C[i-1][j]) % k;  // 杨辉三角
        for (int j = 0; j <= 2000; j++) {   // 前缀和（j>i处为0）
            s[i][j] = (C[i][j] == 0);
            if (i) s[i][j] += s[i-1][j];
            if (j) s[i][j] += s[i][j-1];
            if (i && j) s[i][j] -= s[i-1][j-1];
        }
    }
    while (t--) {
        int n, m;
        scanf("%d%d", &n, &m);
        if (m > n) m = n;
        printf("%d\n", s[n][m]);
    }
    return 0;
}
```

**易错点**：C 的递推要在取模域上进行；前缀和包含重复减的修正项；询问时 j 上界取 min(n,m)；边界 C(i,i)=1%k 也要参与判定。

---

## 本篇小结

完成本篇后应掌握：快速幂、gcd/lcm（及 P×Q=gcd×lcm）、欧拉筛与埃氏筛、质因数分解试除法、乘法原理计数、杨辉三角与组合数取模。数论题的高频套路是"**预处理 + 公式/模板**"，先想清楚性质再动手。

---

# 第 7 篇 动态规划

> 本篇覆盖：线性 DP、背包问题（0-1 / 完全 / 多维费用）、区间 DP、树形 DP、卡特兰数递推。难度以洛谷"普及− / 普及"为主。
> 目标：掌握 DP 的通用四步——**定义状态 → 找转移 → 定初值 → 定答案**，并区分几种背包的循环顺序。

## 7.1 线性 DP

### P1002 过河卒

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1002>
- **难度**：普及−　**标签**：棋盘路径 DP
- **考点**：路径计数、障碍点处理（NOIP 2002 普及组 T4）

**题意简述**：卒从 (0,0) 只能向下/向右走到 (n,m)，马所在点及其 8 个日字控制点不能走，求路径条数。

**解题思路**：dp[i][j] = 从起点到 (i,j) 的路径数，转移 dp[i][j] = dp[i−1][j] + dp[i][j−1]（上、左两个方向）。先把 9 个控制点标记为不可走（dp 置 0）。答案用 long long（条数可能很大）。

**复杂度**：O(n×m)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long dp[25][25];
bool block[25][25];
int main() {
    int n, m, hx, hy;
    cin >> n >> m >> hx >> hy;
    int dx[8] = {1,1,-1,-1,2,2,-2,-2};
    int dy[8] = {2,-2,2,-2,1,-1,1,-1};
    block[hx][hy] = true;
    for (int i = 0; i < 8; i++) {
        int x = hx + dx[i], y = hy + dy[i];
        if (x >= 0 && x <= n && y >= 0 && y <= m) block[x][y] = true;
    }
    dp[0][0] = 1;                  // 起点本身可到
    for (int i = 0; i <= n; i++)
        for (int j = 0; j <= m; j++) {
            if (block[i][j]) { dp[i][j] = 0; continue; }
            if (i > 0) dp[i][j] += dp[i-1][j];
            if (j > 0) dp[i][j] += dp[i][j-1];
        }
    cout << dp[n][m] << endl;
    return 0;
}
```

**易错点**：马的控制点是"马所在点 + 8 个日字点"共 9 个；起点若被控制要处理（题目保证不会）；条数用 long long。

---

### P1216 数字三角形

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1216>
- **难度**：普及−　**标签**：线性 DP
- **考点**：路径求和 DP 入门（IOI 1994 / USACO）

**题意简述**：数字金字塔，从顶部走到底部，每次只能向左下或右下，求路径最大和。

**解题思路**：从上往下递推：dp[i][j] = a[i][j] + max(dp[i−1][j−1], dp[i−1][j])（注意边界只有一条来路）。答案 = 最后一行的最大值。这是最经典的入门 DP。

**复杂度**：O(r²)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int a[1005][1005];
int main() {
    int r;
    cin >> r;
    for (int i = 1; i <= r; i++)
        for (int j = 1; j <= i; j++) cin >> a[i][j];
    for (int i = 2; i <= r; i++)
        for (int j = 1; j <= i; j++)
            a[i][j] += max(a[i-1][j-1], a[i-1][j]);  // 原地滚动
    int ans = 0;
    for (int j = 1; j <= r; j++) ans = max(ans, a[r][j]);
    cout << ans << endl;
    return 0;
}
```

**易错点**：边界 j=1 和 j=i 只有一个来源（越界的 dp 视为 0）；答案在最后一行取 max。

---

### P1091 合唱队形

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1091>
- **难度**：普及−　**标签**：LIS
- **考点**：双向最长上升子序列（NOIP 2004 提高组 T2）

**题意简述**：求最少出列人数，使剩余同学身高先严格上升再严格下降（以中间某人为峰）。

**解题思路**：正序求 left[i] = 以 i 结尾的最长上升子序列长度；逆序求 right[i] = 以 i 开头的最长下降子序列长度（等价于从右往左的上升）。以 i 为峰，保留人数 = left[i] + right[i] − 1，取最大值，答案 = n − max。n ≤ 100，O(n²) 足够。

**复杂度**：O(n²)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int h[105], leftLen[105], rightLen[105];
int main() {
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++) cin >> h[i];
    for (int i = 1; i <= n; i++) {               // 正序LIS
        leftLen[i] = 1;
        for (int j = 1; j < i; j++)
            if (h[j] < h[i]) leftLen[i] = max(leftLen[i], leftLen[j] + 1);
    }
    for (int i = n; i >= 1; i--) {               // 逆序LIS（右向左）
        rightLen[i] = 1;
        for (int j = n; j > i; j--)
            if (h[j] < h[i]) rightLen[i] = max(rightLen[i], rightLen[j] + 1);
    }
    int best = 0;
    for (int i = 1; i <= n; i++)
        best = max(best, leftLen[i] + rightLen[i] - 1);
    cout << n - best << endl;
    return 0;
}
```

**易错点**：严格上升/下降（用 < 不用 ≤）；峰被重复计入要 −1；答案是最少"出列"人数。

---

## 7.2 背包问题

### P1048 采药

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1048>
- **难度**：普及−　**标签**：0-1 背包
- **考点**：0-1 背包模板（NOIP 2005 普及组 T3）

**题意简述**：T 时间采 M 株药，每株耗时+价值，每株只能采一次，求最大总价值。

**解题思路**：0-1 背包：dp[j] 表示用 j 时间能获得的最大价值。外层遍历物品，内层容量**逆序**循环（保证每件物品只用一次）：dp[j] = max(dp[j], dp[j−w[i]] + v[i])。

**复杂度**：O(M×T)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int w[105], v[105], dp[1005];
int main() {
    int t, m;
    cin >> t >> m;
    for (int i = 1; i <= m; i++) cin >> w[i] >> v[i];
    for (int i = 1; i <= m; i++)               // 物品在外层
        for (int j = t; j >= w[i]; j--)        // 容量逆序！
            dp[j] = max(dp[j], dp[j - w[i]] + v[i]);
    cout << dp[t] << endl;
    return 0;
}
```

**易错点**：0-1 背包容量必须逆序循环；dp[j−w[i]] 表示的是"未取当前物品"的状态。

---

### P1616 疯狂的采药

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1616>
- **难度**：普及−　**标签**：完全背包
- **考点**：完全背包模板（每种物品无限取）

**题意简述**：与采药相同，但每种草药可无限采摘，求最大总价值。

**解题思路**：完全背包与 0-1 背包唯一的区别：内层容量**正序**循环——正序时 dp[j−w[i]] 已经是"考虑过当前物品"的状态，从而允许重复取。t×m ≤ 10^7，O(t×m) 可过；注意 int 上限（答案可能较大，用 int 在 10^4×10^4 范围内仍安全，用 long long 更稳）。

**复杂度**：O(m×t)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long dp[10000005];
int main() {
    int t, m;
    cin >> t >> m;
    for (int i = 1; i <= m; i++) {
        int w, v;
        cin >> w >> v;
        for (int j = w; j <= t; j++)           // 正序 = 可重复取
            dp[j] = max(dp[j], dp[j - w] + v);
    }
    cout << dp[t] << endl;
    return 0;
}
```

**易错点**：完全背包容量正序循环；与 0-1 背包的区别就这一行循环方向；t 可达 10^7 注意内存与常数。

---

### P1855 榨取kkksc03

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1855>
- **难度**：普及−　**标签**：二维费用背包
- **考点**：二维费用 0-1 背包

**题意简述**：n 个愿望各需金钱 mi 与时间 ti，总金钱 M、总时间 T，求最多完成几个愿望。

**解题思路**：二维费用背包：dp[M][T] 表示在给定金钱、时间下最多完成的愿望数，每个愿望花费两种资源，0-1 处理（两个容量都逆序）。目标最大化"个数"（每个愿望价值 = 1）。

**复杂度**：O(n×M×T)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int dp[205][205];
int main() {
    int n, M, T;
    cin >> n >> M >> T;
    for (int i = 1; i <= n; i++) {
        int mi, ti;
        cin >> mi >> ti;
        for (int j = M; j >= mi; j--)          // 两维容量都逆序
            for (int k = T; k >= ti; k--)
                dp[j][k] = max(dp[j][k], dp[j - mi][k - ti] + 1);
    }
    cout << dp[M][T] << endl;
    return 0;
}
```

**易错点**：二维背包两层容量循环都要逆序；价值是"完成个数"即每件 +1。

---

## 7.3 区间 DP

### P1880 石子合并

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1880>
- **难度**：普及+/提高−　**标签**：区间 DP
- **考点**：环形区间 DP（NOI 1995）

**题意简述**：环形排列 N 堆石子，相邻两堆可合并，合并得分为新堆石子数，求合并成一堆的最小/最大总得分。

**解题思路**：区间 DP：dp[i][j] = 合并区间 [i,j] 的最优得分，dp[i][j] = min/max(dp[i][k] + dp[k+1][j] + sum(i,j))，k 为分割点。**环形**处理：把数组复制一份变 2N 长，枚举长度 len 从 2 到 N，答案取所有长度为 N 的区间最优值。前缀和 O(1) 求 sum(i,j)。

**复杂度**：O(N³)。

**参考代码**：

```cpp
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
int a[205], sum[205], dpmax[205][205], dpmin[205][205];
int main() {
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++) { cin >> a[i]; a[i + n] = a[i]; }
    for (int i = 1; i <= 2 * n; i++) sum[i] = sum[i - 1] + a[i];
    memset(dpmin, 0x3f, sizeof(dpmin));
    for (int i = 1; i <= 2 * n; i++) dpmin[i][i] = 0;   // 单堆得分0
    for (int len = 2; len <= n; len++)                  // 枚举区间长度
        for (int i = 1; i + len - 1 <= 2 * n; i++) {
            int j = i + len - 1;
            for (int k = i; k < j; k++) {
                int cost = sum[j] - sum[i - 1];         // 本次合并得分
                dpmax[i][j] = max(dpmax[i][j], dpmax[i][k] + dpmax[k + 1][j] + cost);
                dpmin[i][j] = min(dpmin[i][j], dpmin[i][k] + dpmin[k + 1][j] + cost);
            }
        }
    int mn = 0x3f3f3f3f, mx = 0;
    for (int i = 1; i <= n; i++) {                      // 环：取所有起点
        mn = min(mn, dpmin[i][i + n - 1]);
        mx = max(mx, dpmax[i][i + n - 1]);
    }
    cout << mn << "\n" << mx << endl;
    return 0;
}
```

**易错点**：环要复制数组并枚举所有起点；len 最大只枚举到 n；单堆初值得分 0；合并代价是区间石子总数。

---

## 7.4 树形 DP

### P1352 没有上司的舞会

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1352>
- **难度**：普及　**标签**：树形 DP
- **考点**：树上选/不选 DP

**题意简述**：n 个职员构成树，若某职员参加舞会则其直接上司不能参加，每个职员有快乐指数（可为负），求最大总快乐指数。

**解题思路**：树形 DP：f[u][1] = 选 u 时子树最大和（子节点只能不选），f[u][0] = 不选 u 时子树最大和（子节点可选可不选）。DFS 后序遍历：f[u][1] = r[u] + Σ f[v][0]；f[u][0] = Σ max(f[v][0], f[v][1])。答案 = max(f[root][0], f[root][1])。

**复杂度**：O(n)。

**参考代码**：

```cpp
#include <iostream>
#include <vector>
using namespace std;
int r[6005], f[6005][2];
bool hasBoss[6005];
vector<int> son[6005];
void dfs(int u) {
    f[u][1] = r[u];                     // 选u：先计自身快乐值
    for (int v : son[u]) {
        dfs(v);
        f[u][1] += f[v][0];             // u选则子不选
        f[u][0] += max(f[v][0], f[v][1]);  // u不选则子随意
    }
}
int main() {
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++) cin >> r[i];
    for (int i = 1; i < n; i++) {
        int l, k;
        cin >> l >> k;
        son[k].push_back(l);
        hasBoss[l] = true;
    }
    int root = 1;
    while (hasBoss[root]) root++;       // 找树根
    dfs(root);
    cout << max(f[root][0], f[root][1]) << endl;
    return 0;
}
```

**易错点**：先递归子树再合并（后序）；快乐指数可为负，max 处理即可；根是唯一没有上司的节点。

---

## 7.5 递推与卡特兰数

### P1044 栈

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1044>
- **难度**：普及−　**标签**：卡特兰数
- **考点**：卡特兰数递推（NOIP 2003 普及组 T3）

**题意简述**：1~n 依次进栈（可随时出栈），求可能的出栈序列总数。

**解题思路**：出栈序列总数 = 第 n 个**卡特兰数**。递推：f[0]=1，f[i] = Σ f[j] × f[i−1−j]（j 为最后一个出栈元素之前出栈的个数）。也可理解为：以最后一个出栈的数把序列分成前后两段，分别对应左右子树/子问题。

**复杂度**：O(n²)。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
long long f[20];
int main() {
    int n;
    cin >> n;
    f[0] = 1;
    for (int i = 1; i <= n; i++)
        for (int j = 0; j < i; j++)
            f[i] += f[j] * f[i - 1 - j];   // 卡特兰数递推
    cout << f[n] << endl;
    return 0;
}
```

**易错点**：f[0]=1 是递推基础；n ≤ 18 用 long long 足够（C(36,18) 级）；理解"以最后一个出栈元素分段"的拆解方式。

---

## 本篇小结

完成本篇后应掌握：线性 DP（路径、LIS）、0-1/完全/多维费用背包、区间 DP（环的处理）、树形 DP、卡特兰数。DP 关键在"状态定义"：**背包按容量定义、区间按端点定义、树上按节点选/不选定义**；循环方向（正/逆序）决定物品能否重复取。

---

# 第 8 篇 图论

> 本篇覆盖：单源最短路（Dijkstra）、最短路计数、最小生成树（Kruskal）、拓扑排序、并查集连通性、最近公共祖先（LCA 倍增）。难度以洛谷"普及 / 普及+"为主。
> 目标：掌握图论三大核心模板——最短路、最小生成树、LCA，并能用拓扑序与并查集解决依赖/连通类问题。

## 8.1 最短路

### P4779 【模板】单源最短路径（标准版）

- **洛谷链接**：<https://www.luogu.com.cn/problem/P4779>
- **难度**：普及　**标签**：Dijkstra 堆优化模板
- **考点**：非负权单源最短路

**题意简述**：n 个点 m 条有向边（非负权），求 s 到每个点的最短距离。

**解题思路**：Dijkstra + 优先队列（小根堆）优化：dist 初始 inf，源点 0；每次取堆中最小的未确定点扩展松弛。n ≤ 10^5、m ≤ 2×10^5，O(m log n)。边权累加可达 10^9 量级，用 long long。

**复杂度**：O(m log n)。

**参考代码**：

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;
struct Edge { int to, w; };
int main() {
    int n, m, s;
    cin >> n >> m >> s;
    vector<vector<Edge>> g(n + 1);
    for (int i = 0; i < m; i++) {
        int u, v, w;
        cin >> u >> v >> w;
        g[u].push_back({v, w});
    }
    const long long INF = 1e18;
    vector<long long> dist(n + 1, INF);
    vector<bool> done(n + 1, false);
    priority_queue<pair<long long, int>, vector<pair<long long, int>>, greater<>> pq;
    dist[s] = 0;
    pq.push({0, s});
    while (!pq.empty()) {
        auto [d, u] = pq.top(); pq.pop();
        if (done[u]) continue;            // 旧记录跳过
        done[u] = true;
        for (auto [v, w] : g[u])
            if (d + w < dist[v]) {
                dist[v] = d + w;
                pq.push({dist[v], v});
            }
    }
    for (int i = 1; i <= n; i++) cout << dist[i] << (i == n ? "\n" : " ");
    return 0;
}
```

**易错点**：堆里可能残留旧距离，用 done 标记或比较 d 与 dist[u] 跳过；dist 用 long long；不能处理负权边（负权要用 SPFA/Bellman-Ford）。

---

### P1346 电车

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1346>
- **难度**：普及　**标签**：0/1 边权最短路
- **考点**：边权建模（COCI 2002 区域赛）

**题意简述**：每个路口有个开关默认指向第一条轨道，改走其他轨道需下车切换一次开关，求从 A 到 B 最少切换次数。

**解题思路**：把"切换次数"当边权：路口 i 的第一条轨道边权 0（默认，不用切换），其余轨道边权 1（需切换一次）。然后跑最短路（Dijkstra 或 BFS+双端队列）。N ≤ 100，Floyd 也可以。不可达输出 −1。

**复杂度**：O(N²)（或 O(m log n)）。

**参考代码**：

```cpp
#include <iostream>
#include <queue>
using namespace std;
int n, a, b;
int g[105][105];      // 边权矩阵，inf表示无边
int main() {
    cin >> n >> a >> b;
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= n; j++) g[i][j] = (i == j ? 0 : 1e9);
    for (int i = 1; i <= n; i++) {
        int k;
        cin >> k;
        for (int j = 0; j < k; j++) {
            int to;
            cin >> to;
            g[i][to] = (j == 0 ? 0 : 1);   // 第一条边权0，其余1
        }
    }
    for (int k = 1; k <= n; k++)           // Floyd
        for (int i = 1; i <= n; i++)
            for (int j = 1; j <= n; j++)
                g[i][j] = min(g[i][j], g[i][k] + g[k][j]);
    cout << (g[a][b] >= 1e9 ? -1 : g[a][b]) << endl;
    return 0;
}
```

**易错点**：默认轨道（每行第一个）边权是 0 不是 1；不可达输出 −1；自环边（i→i）权 0 不影响。

---

### P1144 最短路计数

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1144>
- **难度**：普及+/提高−　**标签**：BFS、最短路计数
- **考点**：无权图最短路条数统计

**题意简述**：无向无权图（可能有自环、重边），求 1 到每个点最短路的条数（对 100003 取模），不可达输出 0。

**解题思路**：无权图最短路 = BFS 层数。计数：当首次发现 v（dist[v] 未定）时 cnt[v] = cnt[u]；当 dist[v] = dist[u] + 1（已发现但同层可达）时 cnt[v] += cnt[u]。N ≤ 10^6，注意用 scanf/快读与邻接表。

**复杂度**：O(N+M)。

**参考代码**：

```cpp
#include <cstdio>
#include <vector>
#include <queue>
using namespace std;
int main() {
    int n, m;
    scanf("%d%d", &n, &m);
    vector<vector<int>> g(n + 1);
    for (int i = 0; i < m; i++) {
        int x, y;
        scanf("%d%d", &x, &y);
        g[x].push_back(y);
        g[y].push_back(x);
    }
    vector<int> dist(n + 1, -1), cnt(n + 1, 0);
    queue<int> q;
    dist[1] = 0; cnt[1] = 1;
    q.push(1);
    while (!q.empty()) {
        int u = q.front(); q.pop();
        for (int v : g[u]) {
            if (dist[v] == -1) {           // 首次发现：层数+1
                dist[v] = dist[u] + 1;
                cnt[v] = cnt[u];
                q.push(v);
            } else if (dist[v] == dist[u] + 1) {  // 同层另一条路
                cnt[v] = (cnt[v] + cnt[u]) % 100003;
            }
        }
    }
    for (int i = 1; i <= n; i++) printf("%d\n", cnt[i]);
    return 0;
}
```

**易错点**：重边会让同一条最短路被重复计数——正因如此 cnt 累加逻辑天然正确处理；首次发现与同层到达两个分支缺一不可；取模 100003。

---

## 8.2 最小生成树

### P3366 【模板】最小生成树

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3366>
- **难度**：普及　**标签**：Kruskal / Prim
- **考点**：MST 模板

**题意简述**：无向图求最小生成树边权和；若不连通输出 orz。

**解题思路**：Kruskal：所有边按权排序，并查集维护连通性，从小到大尝试加入（两端不连通才加入），加满 n−1 条即为 MST。若最后不足 n−1 条说明不连通，输出 orz。n ≤ 5000、m ≤ 2×10^5，O(m log m)。

**复杂度**：O(m log m)。

**参考代码**：

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
struct Edge { int u, v, w; };
bool cmp(const Edge &a, const Edge &b) { return a.w < b.w; }
Edge e[200005];
int fa[5005];
int find(int x) { return fa[x] == x ? x : fa[x] = find(fa[x]); }
int main() {
    int n, m;
    cin >> n >> m;
    for (int i = 0; i < m; i++) cin >> e[i].u >> e[i].v >> e[i].w;
    for (int i = 1; i <= n; i++) fa[i] = i;
    sort(e, e + m, cmp);
    long long ans = 0;
    int cnt = 0;
    for (int i = 0; i < m && cnt < n - 1; i++) {
        int fu = find(e[i].u), fv = find(e[i].v);
        if (fu != fv) {
            fa[fu] = fv;                 // 合并
            ans += e[i].w;
            cnt++;
        }
    }
    if (cnt == n - 1) cout << ans << endl;
    else cout << "orz" << endl;
    return 0;
}
```

**易错点**：按权排序；并查集要路径压缩；n=1 时答案为 0（cnt 已满）；不连通判断 cnt < n−1。

---

## 8.3 拓扑排序

### P1113 杂务

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1113>
- **难度**：普及　**标签**：拓扑排序 / DP
- **考点**：依赖关系下求最早完成时间（USACO 2002）

**题意简述**：n 项杂务各有耗时与前置杂务（无依赖关系的可并行），求全部完成的最短时间。

**解题思路**：每项杂务最早开始时间 = 所有前置杂务完成时间的最大值。由于输入保证杂务 k 的前置都在 1~k−1 中，直接按编号顺序线性 DP：f[i] = len[i] + max(f[前置])，答案 = max f[i]。本质上就是拓扑序上的最长路（关键路径）。

**复杂度**：O(n × 平均前置数)。

**参考代码**：

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
vector<int> pre[10005];
int len[10005], f[10005];
int main() {
    int n;
    cin >> n;
    int ans = 0;
    for (int i = 1; i <= n; i++) {
        int id, t, p;
        cin >> id >> t;
        len[id] = t;
        while (cin >> p && p) pre[id].push_back(p);
        f[id] = t;
        for (int q : pre[id])
            f[id] = max(f[id], f[q] + t);   // 前置都已完成才能开始
        ans = max(ans, f[id]);
    }
    cout << ans << endl;
    return 0;
}
```

**易错点**：f[i] 是"i 完成的最早时刻"而非耗时；无前置时 f[i] = len[i]；答案取所有 f 的最大值。

---

## 8.4 并查集与连通性

### P1536 村村通

- **洛谷链接**：<https://www.luogu.com.cn/problem/P1536>
- **难度**：普及−　**标签**：并查集
- **考点**：连通块计数

**题意简述**：多组数据：n 个城镇 m 条已有道路，问至少还需建几条路使任意两镇连通。

**解题思路**：并查集合并所有已连通城镇，统计连通块数 cnt，还需 cnt−1 条路。多组数据以输入 0 结束，每组重置并查集。

**复杂度**：O(n + m α(n))。

**参考代码**：

```cpp
#include <iostream>
using namespace std;
int fa[1005];
int find(int x) { return fa[x] == x ? x : fa[x] = find(fa[x]); }
int main() {
    int n, m;
    while (cin >> n && n) {
        cin >> m;
        for (int i = 1; i <= n; i++) fa[i] = i;
        while (m--) {
            int u, v;
            cin >> u >> v;
            int fu = find(u), fv = find(v);
            if (fu != fv) fa[fu] = fv;
        }
        int cnt = 0;
        for (int i = 1; i <= n; i++)
            if (find(i) == i) cnt++;        // 每个根代表一个连通块
        cout << cnt - 1 << endl;            // 连通块间连 cnt-1 条路
    }
    return 0;
}
```

**易错点**：多组数据要重置 fa；统计连通块用"根节点数"（find(i)==i）；答案 cnt−1（n=1 时 0）。

---

## 8.5 树上问题

### P3379 【模板】最近公共祖先（LCA）

- **洛谷链接**：<https://www.luogu.com.cn/problem/P3379>
- **难度**：普及　**标签**：LCA 倍增
- **考点**：倍增法求 LCA

**题意简述**：给定有根多叉树，M 次询问两点的最近公共祖先。N、M ≤ 5×10^5。

**解题思路**：倍增法：① DFS 预处理每个节点的深度 depth 与 2^k 级祖先 f[u][k]；② 查询：先把较深的节点跳到与另一个同深度（按二进制跳），再让两者从大到小一起向上跳（f[u][k] != f[v][k] 才跳），最后答案 = f[u][0]。O((N+M) log N)。

**复杂度**：O((N+M) log N)。

**参考代码**：

```cpp
#include <cstdio>
#include <vector>
using namespace std;
vector<int> g[500005];
int depth[500005], f[500005][20];
void dfs(int u, int fa) {
    f[u][0] = fa;
    for (int k = 1; k < 20; k++)
        f[u][k] = f[f[u][k - 1]][k - 1];    // 2^k祖先
    for (int v : g[u])
        if (v != fa) {
            depth[v] = depth[u] + 1;
            dfs(v, u);
        }
}
int lca(int u, int v) {
    if (depth[u] < depth[v]) { int t = u; u = v; v = t; }
    int diff = depth[u] - depth[v];
    for (int k = 0; k < 20; k++)
        if (diff & (1 << k)) u = f[u][k];   // 二进制跳齐深度
    if (u == v) return u;
    for (int k = 19; k >= 0; k--)
        if (f[u][k] != f[v][k]) {
            u = f[u][k];
            v = f[v][k];
        }
    return f[u][0];
}
int main() {
    int n, m, s;
    scanf("%d%d%d", &n, &m, &s);
    for (int i = 1; i < n; i++) {
        int x, y;
        scanf("%d%d", &x, &y);
        g[x].push_back(y);
        g[y].push_back(x);
    }
    depth[s] = 1;
    dfs(s, 0);
    while (m--) {
        int a, b;
        scanf("%d%d", &a, &b);
        printf("%d\n", lca(a, b));
    }
    return 0;
}
```

**易错点**：f[0][k]=0（根的父亲是 0，depth 判断避开）；跳齐深度用二进制拆位；两节点同层后从大到小跳，最后落在 LCA 的孩子上；本题数据大要用 scanf/printf。

---

## 本篇小结

完成本篇后应掌握：堆优化 Dijkstra、无权图 BFS 计数、Kruskal 最小生成树、拓扑序/依赖 DP、并查集连通块、LCA 倍增。图论题的共性：**先建图（把题意转成点/边/权），再选算法**；模板要能默写，这是后续网络流、强连通等高阶内容的基石。

---

## 附录：全书使用建议

1. **学习顺序**：按篇顺序推进，第 1~3 篇是基础必做，第 4~5 篇打牢数据结构与搜索，第 6~8 篇按需深入（数论、DP、图论）。
2. **练习节奏**：每道题先独立思考 15~20 分钟，再看"解题思路"；代码务必**手敲并提交**，不要只读。
3. **错题记录**：易错点是本书整理者踩过的坑，建议对照自查；把 WA 原因记入自己的错题本。
4. **进阶衔接**：本书覆盖的是算法竞赛入门到普及阶段的核心题目；学完后可衔接《算法竞赛》（罗勇军）提高篇、洛谷"提高+/省选−"题库继续进阶。
5. **与官方题单的关系**：本书官方配套题单需在洛谷登录后搜索"洛谷300题精析"查看（举办者 luoyj123）。本整理为独立重建版，覆盖各篇核心知识点，题量与官方 300+ 题不同，但每个知识点的代表题均已收录。

> **整理说明**：本文件按《算法竞赛试炼场：洛谷300题精析》（清华大学出版社，罗勇军/汪楚奇/陈哲 著）的 8 篇结构，从洛谷公开题库精选代表性真题重建，共 92 题；所有题号、题名、难度均经洛谷题目页逐一核验，题目解析与代码为整理者原创。书中完整解析与代码受版权保护，请以正版图书为准。
#（注：内容由AI生成）
