# js_06_20201203
javascript_regExp_유효성 체크_timer


<!-- 
~~~~~~~~~~~~~~~~~~~~~~~~
js_14.html
~~~~~~~~~~~~~~~~~~~~~~~~
	=> [RegExp 객체]의 기능을 숙지하자
	=> RegExp 객체 기능은 [문자열의 패턴]을 점검하는 것이다.
	=> 실질적으로 입력양식에 입력되거나 선택된 데이터를
		DB에 올바르게 저장하기 위해 사전에 검사하는 [유효성 체크] 시 사용하면 편하다.

 	=> [유효성 체크]란?
 		웹 상에서 클라이언트가 입력 또는 선택한 데이터가 DB에 저장할 합당한
 		데이터인지 검사하는 행위를 말한다.
 		DB 설계와 다른 데이터를 DB에 저장할 수는 없다.
     -->
     
     
    <!DOCTYPE html>
    <html>
    <meta charset="utf-8">
    <head>
      <title></title>
      <script type="text/javascript">
		
		function checkJumin_num(jumin_num){

			if(jumin_num.indexOf("-")>=0){
				return new RegExp(/-[13]/).test(jumin_num);
			}
			else{

				return new RegExp(/^......[13]/).test(jumin_num);
			}
		}

	</script>



</head>
<body>

	<script type="text/javascript">
		

		//-----------------------
		// 검사할 아이디를 변수에 저장하기
		//-----------------------	
		var id = "abc12";



		//-----------------------
		// 아래 규정에 맞는 아이디의 패턴을 관리하는
		// RegExp 객체를 생성.
		//-----------------------
			// <1> 영어소문자로 시작
			// <2> 영소문자,숫자,_로 구성
			// <3> 길이는 6~15 개
		var regExp = new RegExp(/^[a-z][a-z0-9_]{5,14}$/);
/* 
		[정규 표현식]

		 맨앞엔 /^   : 시작문자는 ^ 오른쪽 걸로
		 [a-z]     : 첫 문자는 a~z 사이의 문자 1개
		 [a-z0-9_] : 두번째 문자는 a~z 또는 0~9 또는 _언더바로.
		 {5,14}    : 왼쪽 문자를 5~14개 반복해라.
		 맨뒤엔 $/   : 끝나는 문자는 & 왼쪽 문자로 끝나라~이얘기야.

		<주의> ^ 가 없으면 시작문자에 대한 규정이 없어진다.
			  아무거나 나와도 된다는 뜻이 된다.
			  뒤에 $기 빠지면 뭘로 끝나도 상관이 없다는 뜻.
*/




		 //--------------------------------
		 // RegExp 객체의 test 메소드를 호출하여
		 // 아이디가 RegExp 객체가 가진 패턴에 맞는지 여부를 얻는다.
		 //--------------------------------
		 var result = regExp.test(id)



		 //--------------------------------
		 // result 변수가 
		 // true 면 아이디 적합 메시지를 가진 alert 상자 띄우기
		 // false 면 아이디 부적합 메시지를 가진 alert 상자 띄우기
		 //--------------------------------
		 if (regExp.test(id)){
		 	document.write( id +"는 올바른 아이디입니다.<hr>");
		 }else{
		 	document.write( id +"는 올바르지 않은 아이디입니다.<hr>");
		 }



		 //--------------------------------
		 // 검사할 암호를 변수에 저장하기
		 //--------------------------------

		 var pwd = "1234fff";




		//-----------------------
		// 아래 규정에 맞는 암호의 패턴을 관리하는
		// RegExp 객체를 생성.
		//-----------------------
			// <1> 영소문자,숫자,_로 구성
			// <2> 길이는 5~13 개
		var regExp = new RegExp(/^[a-z0-9_]{5,13}$/);

		var result = regExp.test(pwd);

		if(result){
			document.write(pwd+"는 암호로 적합.<hr>");
		}else{
			document.write(pwd+"는 암호로 부적합.<hr>");
		}



		//-----------------------
		// 검사할 핸드폰 번호를 변수에 저장하기
		//-----------------------
		var phone = "011-22222-3333";


		//------------------------------
		// 아래 규정에 맞는 핸드폰 번호의 패턴을 관리하는
		// RegExp 객체를 생성.
		//------------------------------
			// 핸드폰 번호 (숫자3개-숫자3~4개-숫자4개)여야 함.
			// 첫 숫자 3개는 010 또는 011 또는 016 또는 017 또는 019여야함.
		var regExp = new RegExp
		(/^(010|011|016|017|019)-[0-9]{3,4}-[0-9]{4}$/);


		//------------------------------
		// RegExp 객체의 test 메소드를 호출하여
		// 핸드폰 번호 RegExp 객체가 가진 패턴에 맞는지 여부를 얻는다.
		//------------------------------
		var result = regExp.test(phone);


		//------------------------------
		//result 변수가 true면 핸드폰 번호 적합메시지를 가진 alert 상자 띄우기
		// false 면 핸드폰 번호 부적합 메시지를 가진 alert 상자 띄우기
		//------------------------------
		if(result){
			document.write(phone+"는 핸드폰 번호로 적합합니다.<hr>");
		}else{
			document.write(phone+"는 핸드폰 번호로 부적합합니다.<hr>");
		}



		//-----------------------
		// 검사할 한글이름을 변수에 저장하기
		//-----------------------
		var stu_name = "차효리";

		//------------------------------
		// 한글 2자 이상 패턴을 관리하는 RegExp 객체를 생성.
		//------------------------------
			// {2, } 2글자 이상
		var regExp = new RegExp
		(/^[가-힣]{2,}$/);

		var result = regExp.test(stu_name);

		if(result){
			document.write(stu_name+"는 한글 이름으로 적합<hr>");
		}else{
			document.write(stu_name+" 는 한글이름으로 부적합<hr>");
		}



		//-----------------------
		// 검사할 한글이름을 변수에 저장하기
		//-----------------------
		var user_name = "absd";

		//------------------------------
		// 한글로만 2자 이상 또는 영문으로만 2자이상인지
		// 여부를 판단해서 alert상자 띄우기
		//------------------------------
		var regExp1 = new RegExp
		(/^[가-힣]{2,}$/);

		var regExp2 = new RegExp
		(/^[A-za-z]{2,}$/);

		var result1 = regExp1.test(user_name);
		var result2 = regExp2.test(user_name);

		if(result1||result2){
			document.write(user_name+"는 이름으로 적합<hr>");
		}else{
			document.write(user_name+" 는 이름으로 부적합<hr>");
		}

		
		//-----------------------------------
		var regExp3 = new RegExp(/^(([가-힣]{2,})|([a-zA-Z]{2,}))$/);
		var result3 = regExp3.test(user_name);
		if(result3){
			document.write(user_name+"는 이름으로 적합<hr>");
		}else{
			document.write(user_name+" 는 이름으로 부적합<hr>");
		}
		//-----------------------------------


//**************************************************
//**************************************************

		//-----------------------------------
		// 검사할 문자열을 변수에 저장하기
		//-----------------------------------
		var str = "   ";

		//-----------------------------------
		// 공백이 1개 이상의 문자열 패턴을 관리하는 RegExp 객체를 생성
		//-----------------------------------
		var regExp = new RegExp(/[ ]{1,}/);
			// /[ ]{1,}/ /^ $/ 꺽음쇠^ 달러$ 기호 필요없다.**
			// 맨앞이든 중앙이건 맨뒤건 공백이 있으면 되니깐.


		//-----------------------------------
		// 공백이 없는 문자열 패턴을 관리하는 RegExp 객체를 생성
		//-----------------------------------
		var regExp_1 = new RegExp(/^[^ ]{1,}$/); 


		//-----------------------------------
		// 공백으로만 이루어진 문자열 패턴을 관리하는 RegExp 객체를 생성
		//-----------------------------------
		var regExp_2 = new RegExp(/^[ ]{1,}$/); 



		//-----------------------------------
		// RegExp 객체의 test 메소드를 호출하여
		// 공백이 1개 이상 있는 패턴에 맞는지 여부를 얻는다.
		//-----------------------------------
		var result = regExp.test(str);
		var result_1 = regExp_1.test(str);
		var result_2 = regExp_2.test(str);

		if (result){

			document.write(str + "는 공백이 1개 이상 있습니다.<hr>");
		}else{
			document.write(str + "는 공백이 1개 이상 없습니다.<hr>");
		}


/*

(/^[^]{1,}$/)       공백이 아닌걸로만 이루어지면 이라는 얘기
(/[ ]{1,}/)  		공백이 하나라도 있으면 이라는 얘기
(/^[ ]{1,}$/)		공백으로만 이루어진    이라는 얘기


*/

//**************************************************
//**************************************************


		//-----------------------------------
		// 검사할 문자열을 변수에 저장하기
		//-----------------------------------
		var emp_name = "김란";

		//-----------------------------------
		// 이름이 2자이고 성이 김씨인 문자열 패턴을 관리하는 
		// RegExp 객체를 생성하시오.
		//-----------------------------------
		var regExp = new RegExp(/^[김][가-힣]$/);


		//-----------------------------------
		// RegExp 객체의 test 메소드를 호출하여
		// 공백이 1개 이상 있는 패턴에 맞는지 여부를 얻는다.
		//-----------------------------------
		var result = regExp.test(emp_name);

		if (result){

			document.write(emp_name + "는 이름이 2자이고 김씨가 맞습니다.<hr>");
		}else{
			document.write(emp_name + "는 맞지 않습니다.<hr>");
		}


//**************************************************
//**************************************************


		//-----------------------------------
		// 검사할 문자열을 변수에 저장하기
		//-----------------------------------
		var jumin_num = "881225-4019111";

		//-----------------------------------
		// 성별이 남자인지를 관리하는 RegExp 객체를 생성하시오
		//-----------------------------------


		// <정답1>
		var regExp = new RegExp(/-[13]/);
		// [] 대괄호 안에는 숫자가 두개붙으면 둘중에 하나다.


		// <정답2>
		var regExp1 = new RegExp(/^.......[13]/);
		// .은 공백포함한 임의의 문자다.


		// <정답3>
		if (jumin_num.indexOf("-1")>=0
			||jumin_num.indexOf("-3")>=0){
			document.write(jumin_num+"는 성별이 남성입니다.<hr>");
		}else{
			document.write(jumin_num+"는 성별이 여성입니다.<hr>");
		}
    document.write("되냐?.<hr>")
		// <정답4>
		// 주민번호 중간에 - 없을 경우
		//-----------------------------------
		// 주민번호를 변수에 저장하기
		//-----------------------------------
		var jumin_num1 = "8812254019111"; 

		//-----------------------------------
		// 만약 checkJumin_num 함수 호출 후 리턴값이 true면
		//-----------------------------------
		if(checkJumin_num(jumin_num1)){
			document.write(jumin_num1+"는 성별이 남성입니다.<hr>")
		}else{
			document.write(jumin_num1+"는 성별이 여성입니다.<hr>")
		}




		//-----------------------------------
		// 주민번호를 변수에 저장하기
		//-----------------------------------
		var jumin_num = "881225-4019111";
		
		//-----------------------------------
		// 만약 checkJumin_num 함수 호출 후 리턴값이 true면
		//-----------------------------------
		if (checkJumin_num(jumin_num)){

			document.write(jumin_num + "성별이 남자입니다.<hr>");
		}else{
			document.write(jumin_num + "성별이 여자입니다.<hr>");
		}







	</script>

    </body>
    </html>

<!-- 
~~~~~~~~~~~~~~~~~~~~~~~~
js_14.html
~~~~~~~~~~~~~~~~~~~~~~~~
	=> [window 객체]의 setTimeout(~,~)메소드와 
	    Location 객체의 replace 메소드로
	    지정한 시간 뒤에 페이지 이동을 한다.

	=> window 객체의 setTimeout 메소드 호출 형식
	   ----------------------------------
	   window.setTimeout( function(){실행구문}, 지정초x1000)
	   window.setTimeout( "실행구문", 지정초x1000)
	   ----------------------------------
	   		지정한 초 뒤에 실행구문을 실행한다.
	   		window 객체의 메위주는 window 라는 변수에 저장되어 제공된다.

	=> Location 객체의 replace 메소드 호출형식
		----------------------------------
		location.replace("이동할 URL 주소")
		----------------------------------
			이동할 URL 주소로 현재 페이지가 바뀐다.
			위 replace 메소드 대신에 아래 처럼 href 속성변수에
			"이동할 URL 주소" 설정해도 현재 페이지가 바뀐다.
			location.href ="이동할 URL 주소"
			Location 객체의 메위주는 location 라는 변수에 저장되어 제공된다.
     -->
     <!-- setTimeout은 윈도우가 갖고있는 메소드.
      자스코딩을 익명함수 안에 집어넣어도 실행이 된다.

      -->


    <!DOCTYPE html>
    <html>
    <meta charset="utf-8">
    <head>
      <title></title>

	<script type="text/javascript">
		

		//---------------------------------------
		// 5초 뒤 현재 페이지에서 "http://www.naver.com" 주소로 페이지 이동하기
		//---------------------------------------
		window.setTimeout('location.replace("http://www.naver.com");',5000
			);


		//---------------------------------------
		// 위 코딩은 아래로도 대체 가능하다.
		//---------------------------------------
		/*
		function timer(){
				
			window.setTimeout(

				'location.replace("http://www.naver.com");',5000
				);
		}
		*/


		function timer2(){
			var url = prompt("5초 뒤 이동할 URL 주소를 입력해주세요","");
			window.setTimeout(
				function(){
					location.replace(url);
				}
				, 1000*5

				);
		}






	</script>



    </head>


<!-- 
--------------------------------
body 태그 안에 onLoad = "자스실행구문" 코드 나오면 아래의 의미이다.
------------------------------------
 -->


    <body onload="timer2();"><center>

	<br><br><br><br><br><br><br><br><br><br>
	<br><br><br><br><br><br><br><br><br><br>
	<br><br>
	잠자는 3시의 공주......



    </body>
    </html>



  
    
    <!-- 
    -------------------------------
    js_16.html
    -------------------------------
      =>Date 객체의 각종 메소드와, 
        Window 객체의 setInterval() 메소드를 사용하여 
        웹화면에 흘러가는 디지털 시계를 출력하자.
     ------------------------------
     -->


    <!DOCTYPE html>
    <html>
    <meta charset="utf-8">
    <head>
      <title></title>

      <script type="text/javascript">

        function getWeek1(weekNo){

          var week = "";

          if(weekNo==0) {week = "일";}
          else if(weekNo==1){week = "월";}	
          else if(weekNo==2){week = "화";}	
          else if(weekNo==3){week = "수";}	
          else if(weekNo==4){week = "목";}	
          else if(weekNo==5){week = "금";}	
          else if(weekNo==6){week = "토";}	
          return week;
        }

        //------------------------------
        // 웹 화면에 현재 시스템 시간을 출력하는 함수 선언 
        //------------------------------
        function showTime(){

          // 현재 날짜를 관리하는 Date() 객체 생성
          var today = new Date();
          // Date 객체에서 날짜관련 각 데이터를 꺼내어 저장하기 
          var amt = "오전";
          var pmt = "오후";
          var am_pm = "";
          var year = today.getFullYear();
          var month = today.getMonth()+1;
          var date = today.getDate() ;
          var day = getWeek1(today.getDay());
          var hour = today.getHours();
          var minutes = today.getMinutes();
          var seconds = today.getSeconds();
          var week = ["일","월","화","수","목","금","토"]
          [today.getDay()];

          //-------------------------------------
          // 오전, 오후 정하고 군대시계를 사제 시간으로 바꾸기
          //-------------------------------------
          if (hour<12){am_pm = amt;}else{am_pm = pmt;}

          if (hour>12) {hour = hour - 12;}

          //-------------------------------------
          // 월,일,시,분,초 데이터가 10미만이면 앞에 0 붙이기
          //-------------------------------------
          if (date <10){date = "0"+ date;}

          if (month<10) {month = "0"+ month;}	

          if (hour<10) {hour = "0" + hour;}

          if (minutes<10){minutes = "0"+minutes;}

          if (seconds<10){seconds = "0"+seconds;}

          //-------------------------------------
          // id="nowTime" 가 있는 태그 영역 내부에 시간 문자열 삽입.
          //-------------------------------------
          // getElementById(id값). div태그를 관리하는 element 객체.
          // .innerHTML div태그 안에 id값을 집어 넣는 것
          //-------------------------------------
          // document.getElementById(div태그의"id값").innerHTML = 문자열;
          //-------------------------------------

          document.getElementById("nowTime").innerHTML = 
          "<h2>NAVER</h2>"
          +"<hr>"+
          year +"년 "+month+"월 "+ date +"일("+week +") "+am_pm+" "+ hour +"시 "+minutes +"분 "+seconds+"초";

        }

          //-------------------------------------
          // 1초마다 showTime() 함수를 호출하는 함수 선언
          //-------------------------------------
          function startTime(){
            window.setInterval( function(){showTime();},1*1000);
          }



      </script>
    </head>
    <!----------------------------------------
     body 태그 안의 내용을 모두 읽어 실행한 후 startTime() 란 함수 호출하라
    ------------------------------------------>
    <body onLoad="startTime();"><center>

    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br>


      <div id="nowTime"></div>

    </body>
    </html>
    
    <!-- 
    ~~~~~~~~~~~~~~~~~
    js_17.html
    ~~~~~~~~~~~~~~~~~
     -->

    <!DOCTYPE html>
    <html>
    <meta charset="utf-8">
    <head>
      <title></title>

      <script type="text/javascript">



        var num = 5;


        function timer(){

            window.setTimeout('location.replace("http://www.naver.com");',5000
            );

          document.getElementById("second").innerHTML = 
            "초 후에 NAVER로 이동";
        }

        function startTime(){
            window.setInterval( 

              function(){

                timer();

              } 
              , 1*1000
            );
        }

      </script>
    </head>
    <body onload="timer();"><center>


      <span id="second"></span>

    </body>
    </html>
