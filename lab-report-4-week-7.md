# Part 1
* Vim command to change the name of the start parameter and its uses to base
```
:12,30s/start/base/g<Enter>:wq<Enter>
```
<img width="210" alt="Screen Shot 2022-11-12 at 5 44 49 PM" src="https://user-images.githubusercontent.com/78475359/201501561-494327c9-f81c-47c1-92c8-4305ded2e3a4.png">
<img width="428" alt="Screen Shot 2022-11-12 at 5 45 36 PM" src="https://user-images.githubusercontent.com/78475359/201501567-68e7dca3-f14e-4093-9d35-0ee800bc29a9.png">
<img width="777" alt="Screen Shot 2022-11-12 at 5 46 05 PM" src="https://user-images.githubusercontent.com/78475359/201501576-a8b56719-78ec-44ac-8547-e69e4546310d.png">

* The :s command substitutes patterns. 12,30 means it searches for the pattern from the line 12 to 30 (the FilerHelpers class). If I don't declare the range, it will replace the "start" in "Server.start()" in line 74, which will cause an error.

# Part 2
