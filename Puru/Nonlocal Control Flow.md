
---

**Continue**

- ~={yellow} Skip to next iteration of loop.=~

```c
	continue
```

---

**Break**

- ~={yellow}Terminates a loop/switch=~

```c
	break;
```

---

**Return**

- ~={yellow} Transfers control back to the caller of a function.=~

```c
	return;
```

---

**Switch**

- ~={yellow}Enumerates cases.=~ ~={red} FALL-THROUGH BEHAVIOR. MUST BREAK. =~
	- `default` runs as a case ~={cyan} ONLY=~ after all cases have been checked;
	- `default` can ~={red}FALL-THROUGH=~ and ~={red}BE FALLEN INTO=~ depending on ~={green}POSITION=~
	
```c
switch (guessedNumber) {
	case (2) : cout << "Wrong!"; break;
	case (3) : cout << "Wrong!"; break;
	case (5) : cout << "Wrong!"; break;
	case (7) : cout << "Right!"; break;
	default:
		cout << "Bad guess.";
		break;
}
```

---
