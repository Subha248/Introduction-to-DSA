### Ques4 : Set the ith bit and turn it into 1.(SET)

## 🎯 Number we’ll use

```
n = 10
```

Binary:

```
10 = 1010
```

Bit positions (right → left):

```
Position: 4 3 2 1
Bits:     1 0 1 0
```

---

# ✅ SETTING a bit (force it to 1)

### Question

👉 **Set the 2nd bit of 10**

---

## STEP 1: Create the mask

Formula:

```
1 << (i - 1)
```

Here:

```
i = 2
1 << 1 = 0010
```

Mask:

```
0010
```

---

## STEP 2: OR the number with the mask

```
n    = 1010
mask = 0010
-------------
       1010
```

Result:

```
1010 = 10
```

👉 2nd bit is now **1** (it already was 1, so no change)

---

### 🔁 Try setting a bit that is 0

👉 **Set the 1st bit of 10**

Mask:

```
1 << 0 = 0001
```

OR:

```
1010
0001
----
1011
```

Result:

```
1011 = 11
```

✅ Bit forced to **1**

---

### 🔑 SET rule (memorize)

```
n | (1 << (i - 1))
```

OR **forces 1**, doesn’t disturb other bits.

---

# ❌ RESETTING a bit (force it to 0)

### Question

👉 **Reset the 3rd bit of 10**

---

## STEP 1: Create set-mask

```
1 << (3 - 1) = 1 << 2 = 0100
```

---

## STEP 2: Flip the mask (complement)

```
~0100 = 1011   (ignore extra bits, focus on pattern)
```

This mask has:

* `0` at position 3
* `1` everywhere else

---

## STEP 3: AND with the number

```
n    = 1010
mask = 1011
-------------
       1010
```

Result:

```
1010 = 10
```

👉 3rd bit was already 0 → stays 0

---

### 🔁 Reset a bit that is 1

👉 **Reset the 4th bit of 10**

Mask before flip:

```
1 << 3 = 1000
```

After flip:

```
0111
```

AND:

```
1010
0111
----
0010
```

Result:

```
0010 = 2
```

✅ 4th bit forced to **0**

---

### 🔑 RESET rule (memorize)

```
n & (~(1 << (i - 1)))
```

AND **forces 0**, keeps others same.

---

## 🧠 Ultra-short memory hack

```
SET   → OR with 1
RESET → AND with 0
```

Mask decides **where**.

---

## 🏁 Final takeaway (no overthinking)

* Mask = control switch
* OR → turn ON
* AND → turn OFF
* Bits you don’t touch stay safe
