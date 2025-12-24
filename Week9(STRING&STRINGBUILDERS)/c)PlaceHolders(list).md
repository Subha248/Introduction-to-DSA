
---

### **1️⃣ Floating-point numbers**

| Placeholder | Meaning                               | Example                         |
| ----------- | ------------------------------------- | ------------------------------- |
| `%f`        | Decimal/float/double                  | `%.2f` → 2 digits after decimal |
| `%e`        | Scientific notation                   | `%.3e` → 3 digits in exponent   |
| `%g`        | General format (automatic `f` or `e`) | `%g`                            |

---

### **2️⃣ Integers**

| Placeholder | Meaning                 | Example      |
| ----------- | ----------------------- | ------------ |
| `%d`        | Decimal integer         | `%d` → `123` |
| `%o`        | Octal                   | `%o` → `173` |
| `%x`        | Hexadecimal (lowercase) | `%x` → `7b`  |
| `%X`        | Hexadecimal (uppercase) | `%X` → `7B`  |

---

### **3️⃣ Characters and Strings**

| Placeholder | Meaning   | Example          |
| ----------- | --------- | ---------------- |
| `%c`        | Character | `%c` → `A`       |
| `%s`        | String    | `%s` → `"hello"` |

---

### **4️⃣ Boolean**

| Placeholder | Meaning | Example                  |
| ----------- | ------- | ------------------------ |
| `%b`        | Boolean | `%b` → `true` or `false` |

---

### **5️⃣ General / Misc**

| Placeholder | Meaning     | Example                                     |
| ----------- | ----------- | ------------------------------------------- |
| `%%`        | Literal `%` | `"Discount: 50%%"` → prints `Discount: 50%` |

---

### **6️⃣ Width & Precision**

* `%5d` → minimum **width 5**, pad spaces
* `%-5d` → left-aligned
* `%.2f` → **2 decimal places**
* `%8.2f` → width 8, 2 decimal places, right-aligned

---

### 🔒 Brain-lock version (just remember this)

* `%d` → integer
* `%f` → float/double
* `%s` → string
* `%c` → char
* `%b` → boolean
* `%%` → percent
* `.N` → precision for decimals
* `width` → minimum field width

---

---


**Extra tip:**

* Always **comma after format string** → supply values for placeholders
* Placeholders are **replaced in order**

Example:

```java
System.out.printf("Hello %s, score: %.1f%%", "Subha", 92.5);
```

Output:

```
Hello Subha, score: 92.5%
```

---

