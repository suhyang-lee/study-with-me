# 📌 DOM 조작하기

## ✅ window.onload = function() vs window.addEventListener("load")
- 협업 시에는 window.onload에 바로 function을 정의하지 않음.
- 혼자 사용할 때는 문제는 없지만, 가급적이면 리스너를 달아 사용하는 것이 좋음.

## ✅ createElement vs innerHTML
- 유지보수의 문제로 innerHTML 을 주로 사용한다.
- createElement를 사용하게되면 가독성이 떨어져 협업을 하기 어려워짐.
- innerHTML 사용 : 보안의 위험성은 있지만 충분히 막을 수 있는 여러 대안이 마련되어있으므로 유지보수 측면에서 고려하는 것이 좋음.

## ✅ getElemnet(s)By ~ vs querySelector
- id 등은 바로 접근하면 위험할 수 있음.
- tagName은 레거시. 
- 주로 querySelector를 사용함. (가장 처음에 일치되는 값을 가져옴)
