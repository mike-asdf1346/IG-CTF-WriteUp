# IG-CTF-game-write-up
**Author: JellyPie (Mike)**
## WARNING: THIS WRITE-UP INCLUDES FLAG!!
### THIS IS THE PROCESS OF THE WHOLE GAME

:unlock: **CTF Write-up｜解答本**

以下為本題的完整解題流程。

### 本題的答案藏在一個IG帳號中的三個貼文內
其中, 有一個貼文洩漏出了這一段文字：
```text
[  0.034100] data: t3w025u6y8y809x98068x9492058y880y92860490870270089x9u729u00949v999
```
找到之後就可以開始解題了

### Step 1 — Identify the Encrypted Code
首先，找出IG新導向的帳號中找出提供的加密字串：

```text
t3w025u6y8y809x98068x9492058y880y92860490870270089x9u729u00949v999
```

### Step 2 — Shift the Characters
觀察字串中的英文字母與數字，將兩者分別向後位移 7 個位置。

解密後得到：

```text
a0d792b3f5f576e65735e6169725f557f69537167547947756e6b496b77616c666
```

### Step 3 — Reverse and Decode
接下來，使用 Linux 指令處理解密後的內容。

將第二步的結果存入 '你要的檔案'，再執行：

```bash
cat '你要的檔案' | rev | xxd -r -p
```

**Command Breakdown**

- `cat`：讀取檔案內容。
- `rev`：將每一行的字元順序反轉。
- `xxd -r -p`：將純十六進位字串轉換回原始位元組。

### Step 4 — Retrieve the Flag
完成上述步驟後，即可得到最終 Flag：

:checkered_flag: **Flag**

```text
flag{iKnewItWasYou_RyanSung__;)}
```

### Conclusion
本題結合了字元位移、字串反轉與十六進位解碼。

解題的關鍵在於：
1. 找出正確的字元位移規則。
2. 將解密後的字串視為十六進位資料。
3. 利用 Linux 指令反轉字串並還原資料。

:closed_lock_with_key: 我也不知道我為什麼要做這個..反正不管怎麼樣, 這是我的第一篇write-up, 也是我第一次把Linux所學的部份知識重新 review 一遍, 最後, 不管你是沒解開或是有解開的，都非常感謝您的遊玩🫰️
