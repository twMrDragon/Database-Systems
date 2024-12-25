# 資料庫系統 hw4

## 資工三 111590012 林品緯

### 1.

#### (a)

$\{A,B,D\}$

測試 $\{A,B,D\}^+$

- $\{A,B\}\rightarrow\{C\}$，所以 $\{A,B,D\}^++=\{A,B,D,C\}$
- $\{B,D\}\rightarrow\{E,F\}$，所以 $\{A,B,D\}^+=\{A,B,D,C,E,F\}$
- $\{A,D\}\rightarrow\{G,H\}$，所以 $\{A,B,D\}^+=\{A,B,D,C,E,F,G,H\}$
- $\{A\}\rightarrow\{I\}$，所以 $\{A,B,D\}^+=\{A,B,D,C,E,F,G,H,I\}$
- $\{H\}\rightarrow\{J\}$，所以 $\{A,B,D\}^+=\{A,B,D,C,E,F,G,H,I,J\}$

而 $\{A,B\},\{B,D\},\{A,D\}$ 的閉包沒有包含所有屬性，所以 $\{A,B,D\}$ 為 key

#### (b)

- $R_1 = \{A, B, C\}$
- $R_2 = \{B, D, E, F\}$
- $R_3 = \{A, D, G, H, J\}$
- $R_4 = \{A, I\}$

#### (c)

- $R_1 = \{A, B, C\}$
- $R_2 = \{B, D, E, F\}$
- $R_3 = \{A, D, G, H\}$
- $R_4 = \{A, I\}$
- $R_5 = \{H, J\}$

### 2.

#### (a)

- 假設 1NF 成立
- 因為 {Course_no} $\rightarrow$ {Offering_dept, Credit_hours, Course_level} 只相依部分 key，所以 2NF 不成立。
- 因為 2NF 不成立，所以 3NF 不成立

Ans:

1NF

#### (b)

{Course_no,Sec_no,Semester,Year} 和 {Room_no,Days_hours,Semester,Year} 為 candidate key

#### (c)

To 2NF:

- $R_1 =$ {Offering_dept, Credit_hours, Course_level}
  - {Course_no} $\rightarrow$ {Offering_dept, Credit_hours, Course_level}
- $R_2 =$ {Course_no, Sec_no, Semester, Year, Days_hours, Room_no, No_of_students, Instructor_ssn}
  - {Course_no, Sec_no, Semester, Year} $\rightarrow$ {Days_hours, Room_no,
    No_of_students, Instructor_ssn}
  - {Room_no, Days_hours, Semester, Year} $\rightarrow$ {Instructor_ssn, Course_no,
    Sec_no}

To 3NF:

沒有遞移依賴，所以跟 2NF 結果一樣

- $R_1 =$ {Offering_dept, Credit_hours, Course_level}
  - {Course_no} $\rightarrow$ {Offering_dept, Credit_hours, Course_level}
- $R_2 =$ {Course_no, Sec_no, Semester, Year, Days_hours, Room_no, No_of_students, Instructor_ssn}
  - {Course_no, Sec_no, Semester, Year} $\rightarrow$ {Days_hours, Room_no,
    No_of_students, Instructor_ssn}
  - {Room_no, Days_hours, Semester, Year} $\rightarrow$ {Instructor_ssn, Course_no,
    Sec_no}

To BCNF:

FD 的右邊沒有全部為 prime attribute，所以跟 3NF 結果一樣

- $R_1 =$ {Offering_dept, Credit_hours, Course_level}
  - {Course_no} $\rightarrow$ {Offering_dept, Credit_hours, Course_level}
- $R_2 =$ {Course_no, Sec_no, Semester, Year, Days_hours, Room_no, No_of_students, Instructor_ssn}
  - {Course_no, Sec_no, Semester, Year} $\rightarrow$ {Days_hours, Room_no,
    No_of_students, Instructor_ssn}
  - {Room_no, Days_hours, Semester, Year} $\rightarrow$ {Instructor_ssn, Course_no,
    Sec_no}

### 3.

#### (a)

$$
\begin{aligned}
R&=30+9+9+40+10+8+1+4+4+1 \\
&=116
\end{aligned}
$$

#### (b)

$$
\begin{aligned}
bfr&=\lfloor \frac{512}{116} \rfloor \\
&=4
\end{aligned}
$$

$$
\begin{aligned}
b&=\lceil \frac{30000}{4} \rceil \\
&=7500
\end{aligned}
$$

#### (c)

##### (i)

$$
\begin{aligned}
bfr_i&=\lfloor \frac{512}{9+6} \rfloor \\
&=34
\end{aligned}
$$

##### (ii)

number of first-level index entries:

$$
\begin{aligned}
&=7500
\end{aligned}
$$

number of first-level index blocks:

$$
\begin{aligned}
&=\lceil \frac{7500}{34} \rceil \\
&= 221
\end{aligned}
$$

##### (iii)

$$
\begin{aligned}
r_1 &= 221 \\
r_2 &= \lceil \frac{221}{34} \rceil \\
&=7 \\
r_3 &= \lceil \frac{7}{34} \rceil \\
&=1
\end{aligned}
$$

level = 3

##### (iv)

$221(r_1)+7(r_2)+1(r_3) = 229$

##### (v)

$3(\text{level})+1(\text{record}) = 4$

#### (d)

使用 Option 2

##### (i)

$$
\begin{aligned}
bfr_i&=\lfloor \frac{512}{9+6} \rfloor \\
&=34
\end{aligned}
$$

##### (ii)

number of first-level index entries:

$$
\begin{aligned}
&=30000
\end{aligned}
$$

number of first-level index blocks:

$$
\begin{aligned}
&=\lceil \frac{30000}{34} \rceil \\
&= 883
\end{aligned}
$$

##### (iii)

$$
\begin{aligned}
r_1 &= 883 \\
r_2 &= \lceil \frac{883}{34} \rceil \\
&=26 \\
r_3 &= \lceil \frac{26}{34} \rceil \\
&=1
\end{aligned}
$$

##### (iv)

$883(r_1)+26(r_2)+1(r_3) = 910$

##### (v)

$3(\text{level})+1(\text{record}) = 4$

### 4.

|                 | primary | secondary                    | clustering |
| --------------- | ------- | ---------------------------- | ---------- |
| 欄位            | 主鍵    | 非主鍵                       | 非主鍵     |
| 唯一性          | 唯一    | 可能重複                     | 可能重複   |
| 存儲順序        | ordered | ordered, unordered or hashed | ordered    |
| dense or sparse | dense   | dense or sparse              | sparse     |
