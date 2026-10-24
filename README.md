# IG-CTF-game-write-up

## ⚠️WARNING: THIS WRITE-UP INCLUDES FLAG!!⚠️
**Author: JellyPie (Mike)**
## **CTF Write-up｜解答本**

以下為本題的完整解題流程。

### 本題的答案藏在一個IG帳號中的三個貼文內
其中, 有一個貼文洩漏出了這一段文字：
```text
[  0.034100] data: 333j38344i363i3l32443641443840463m424946383l40423l344k7h
```
找到之後就可以開始解題了

### STEP 1 — 辨認加密字串 Identify the Encrypted Code
首先，找出原帳號簡介中所提供的秘密帳號並找出裡面提供的加密字串：

```text
333j38344i363i3l32443641443840463m424946383l40423l344k7h
```

### STEP 2 — 置換文字 Shift the Characters
觀察字串中的英文字母與數字，將兩者分別向前位移 7 個位置。
e.g. 'a' ---> 'h' 'b' ---> 'i'
解密後得到：

```text
666c61677b696b6e65776974776173796f757279616e73756e677d0a
```

### STEP 3 — 利用xxd指令 xxd Decode
接下來，可使用 Linux 指令處理解密後的內容。

把結果echo出來並利用導管連接xxd指令：
```bash
echo '666c61677b696b6e65776974776173796f757279616e73756e677d0a' | xxd -r -p
```

OR

將第二步的結果存入 '你要的檔案'，再執行：

```bash
cat '你要的檔案' | xxd -r -p
```

利用網路上的工具轉換也行。

**Command Breakdown**

- `cat`：讀取檔案內容
- `xxd -r`：將十六進制格式轉回二進制格式
- `xxd -p`：輸出純十六進制格式

### Step 4 — Retrieve the Flag
完成上述步驟後，即可得到最終 Flag：

:checkered_flag: **Flag**

```text
flag{iknewitwasyouryansung}
```

### Conclusion
本題結合了字元位移、字串反轉與十六進位解碼。

解題的關鍵在於：
1. 找出貼文內洩漏的字串。
1. 找出正確的字元位移規則。
2. 將解密後的字串視為十六進位資料。
3. 利用 Linux 指令反轉字串並還原資料。

:closed_lock_with_key: 我也不知道我為什麼要做這個.., 這是我的第一篇write-up, 如果有誤還請馬上告訴我, 再次, 謝謝你願意花時間在我的Puzzle上!
