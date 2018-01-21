# JavaScript-Demos
A box that contains my favorite practice demos~

心血来潮，复习一遍JavaScript，顺带做些小案例，将脑瓜子里可能用到的知识、技术都融汇在一起来实现，实在是有趣。

第一个案例：猜数游戏
  1、案例介绍：简单的小游戏，用到了HTML5的新特性---本地存储、警告框、提示输入框、Math对象、ES6的模板字符串、函数封装等知识。
  2、功能介绍：
    (1) 第一次打开游戏界面的时候弹出提示框，向玩家说明游戏规则
    (2) 再来，弹出提示对话框，提示用户输入要猜的数字，并对输入的数字作条件判断：
			 1) 要求为number类型
			 2) 要求不能为空
			 3) 要求在0-100的闭区间范围内的整数
			 4) 当玩家取消输入的时候，不会进行后续的处理
    (3) 用sessionStorage存储当前游戏的猜数次数，实现以下功能：
			 1) 当玩家在每次成功猜中或没猜中数字的时候，给出提示，并告之其当前使用的猜数次数;
			 2) 若在规定猜数限制次数内没猜出数字，游戏结束，猜数次数重记;
			 3) 若玩家猜中数字，游戏结束，猜数次数也重记。
    (4) 当输入正确，给用户提示，告之用了多少次机会猜中数字。
  3、遇到的BUG和解决方案
    (1) Question：上次没结束的游戏影响这次游戏
        Answer：用sessionStorage而不是localStorage
        Thoughts：因为sessionStorage存储的数据在窗口关闭后会自动删除，而localStorage除非人为删除，要不然会是永久存储在浏览器。
    (2) Question：Number(value)，当value是空字符串返回的是"0"
        Answer：加一波判断：当输入为空的时候，赋值给guessNum为NaN
    (3) Question：prompt()取消输入的时候会返回null，传入到Number()里面返回的是0，会影响后面的处理
        Answer：用条件判断，忽略prompt()返回的null

第二个案例：成绩等级评价
   1、案例介绍：原本只需要用到switch来实现的案例，我试图加入了art-template模板引擎的使用、DOM操作、循环语句的使用、函数封装、ES6的箭头函数、数组的reduce方法等等。
   2、功能介绍：
      (1) 以对象模拟JSON文件的数据（原生JS不能直接从问价那种读取内容）
      (2) 用表格展示“学生期末考试成绩表”，用art-template模板打印数据到表格上
      (3) 以原生JS代码获取表格上的数据，封装一个用switch对学生考试成绩判断，并返回成绩等级的函数；封装一个函数，用来统计学生的期末考试总成绩。
      (4) 将经判断、计算等操作获得的成绩等级和学生总成绩再用一个模板渲染到另外一个表格上。
   3、遇到的BUG和解决
      (1) 原生的art-template模板引擎的使用（方法是有很多的，这是其一）：
         1)  写好模板：<script id="tpl" type="text/html">...</script>
         2)  JS代码：
           步骤一 获取模板标签内容：var tpl = document.getElementById("tpl").innerHTML;
           步骤二 准备数据：var data = [{name: "jack"}, {name: "rose"}];
           步骤三 用template函数将数据整合到模板上：var  = template(tpl, {data: data});
           步骤四 将整合好的模板内容渲染到指定的标签上去：document.getElementById("box").innerHTLM = html;
      (2) 计算学生总成绩的函数封装：
         1)  简易方法：使用数组的reduce方法，配合ES6的箭头汗水，代码量十分少，就能够实现。
         2)  代码： 
             function getTotal() {
                // 总和计数器
                const reducer = (accumulator, sum) => accumulator + sum;
                return arr.reduce(reducer);
             } 
         
         
         
