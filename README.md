20180704 

- 자바스크립트 문서는 MDN
- jQuery는W3Schools





- jQuery
      $
      ƒ ( selector, context ) {
      
      		// The jQuery object is actually just the init constructor 'enhanced'
      		// Need init if jQuery is called (just allow error to be thrown if not included)
      		return new jQuery…
          
      $("css 선택자")
      jQuery.fn.init [prevObject: jQuery.fn.init(1), context: document, selector: "css 선택자"]context: documentlength: 0prevObject: jQuery.fn.init [document, context: document]selector: "css 선택자"__proto__: Object(0)
      
      $(".btn") //선택자로 찾는 경우
      jQuery.fn.init(2) [a.btn.btn-primary, a.btn.btn-primary, prevObject: jQuery.fn.init(1), context: document, selector: ".btn"]
          
      $('a') //태그로 찾는 경우
      jQuery.fn.init(4) [a.btn.btn-info, a.btn.btn-primary, a, a, prevObject: jQuery.fn.init(1), context: document, selector: "a"]
          
      $('title') //
      jQuery.fn.init [title, prevObject: jQuery.fn.init(1), context: document, selector: "title"]    
  $('.btn').이벤트명(function(){});형식
      // jQuery를 사용하면 javascript와 다르게 일괄 적용??
      // 모든 버튼에 이벤트가 적용된다.
      $('.btn').mouseover(function(){ 
          alert("건드리지마") 
      });
      jQuery.fn.init(2) [a.btn.btn-primary, a.btn.btn-primary, prevObject: jQuery.fn.init(1), context: document, selector: ".btn"]
      // jQuery를 사용하면 javascript와 다르게 일괄 적용??
      // 모든 버튼에 이벤트가 적용된다.
      //여러가지 이벤트를 늘려나가기 쉬워서 가장 많이 사용한다.
      $('.btn').on('mouseover', function(){
          console.log("건드리지마세요");
      });
          
      jQuery.fn.init(2) [a.btn.btn-info, a.btn.btn-primary, prevObject: jQuery.fn.init(1), context: document, selector: ".btn"]
      4 건드리지마세요 //4는 횟수
  - mouse가 버튼위에 올라갔을 때, 버튼에 있는 btn-primary 클래스를 삭제하고 btn-danger 클래스를 준다. 버튼에서 마우스가 내려왔을때 다시 btn-danger 클래스를 삭제하고 btn-primary 클래스를 추가한다.
    - 여러 개의 이벤트 등록하기
    - 요소에 class를 넣고 뺴는 jQuery function을 찾기.
      function change( event ) {
       $( ".btn" ).attr("class",event.data.name);
      }
      $( ".btn" ).on( "mouseover", {
        name: "btn btn-danger"
      }, change );
      $( ".btn" ).on( "mouseleave", {
        name: "btn btn-primary"
      }, change );
      var btn = $( ".btn" )
      undefined
      btn.on('mouseover mouseleave', function(){
          if(btn.hasClass('btn-danger')){
              btn.removeClass('btn-danger').addClass('btn-primary');
          }else{
          btn.removeClass('btn-primary').addClass('btn-danger');
      }})
      jQuery.fn.init(2) [a.btn.btn-primary, a.btn.btn-primary, prevObject: jQuery.fn.init(1), context: document, selector: ".btn"]
  - toggle 코드??
      var btn = $( ".btn" )
      undefined
      
      // 모든 버튼이 반응한다.
      btn.on('mouseover mouseleave', function(){
          btn.toggleClass('btn-danger').toggleClass('btn-primary');
      });
      jQuery.fn.init(2) [a.btn.btn-primary, a.btn.btn-primary, prevObject: jQuery.fn.init(1), context: document, selector: ".btn"]
  - this
      var btn = $( ".btn" )
      undefined
      // 이벤트가 발생한 바로 그 아이만 실행하도록
      btn.on('mouseover mouseleave', function(){
          $(this).toggleClass('btn-danger').toggleClass('btn-primary');
          console.dir(this);// html태그를 의미한다.
          console.dir($(this));//jQuery 객체를 의미
      });
      jQuery.fn.init(2) [a.btn.btn-primary, a.btn.btn-primary, prevObject: jQuery.fn.init(1), context: document, selector: ".btn"]
  - attr
    - https://www.w3schools.com/jquery/html_attr.asp
  - 버튼에 마우스가 오버됐을때 상단에 있는 이미지의 속성에 style 속성과 width: 100px;의 속성값을 부여한다.
      var btn = $( ".btn" )
      
      btn.on('mouseover', function(){
          $('img').attr('style','width: 100px');     //속성 부여
      });
      
      $('img').attr('style');  //속성 가져오기
      "width: 100px"
  - text
    - text가 있는 상태라면 그냥 바꾸는 식으로
    - 없으면 innertext를 끄집어내서 설정한다.
      btn.on('mouseover', function(){
          $('.card-title').text('건드리지마');
      });
  - sibling
    - 같은 레벨( 같은 부모를 가지는 경우)의 값을 바꾸고 싶은 경우에는 
      $(this).siblings.find("card-title").text("....")	
    - https://www.w3schools.com/jquery/traversing_siblings.asp
    버튼(요소) 에 마우스가 오버 (이벤트)되었을 때 (이벤트 리스너), 이벤트가 발생한 버튼($(this))과 상위 수준(parent)에 있는 요소 중에서 .card-title의 속성을 가진 친구를 찾아 텍스트를 변경시켜준다.
      var btn = $( ".btn" )
      btn.on('mouseover', function(){
          console.log($(this).siblings());
      });
      jQuery.fn.init(4) [h5.card-title, p.card-text, p.card-text, p.card-text, prevObject: jQuery.fn.init(1), context: a.btn.btn-primary]
      
      btn.on('mouseover', function(){ //find는 같은 요소를 찾는 것이 아닌 하위요소를 찾는 것
          console.log($(this).siblings().find('.card-title')); 
      });
      jQuery.fn.init [prevObject: jQuery.fn.init(4), context: a.btn.btn-primary, selector: ".card-title"]
      
      btn.on('mouseover', function(){
          $(this).parent().find('.card-title').text("건드리지마"); 
      });
  
- 텍스트 변환기(오타발생기)
  - index.html
        <textarea id="input" placeholder="변환할 텍스트를 입력해주세요."></textarea>
        <button class="translate">바꿔줘</button>
        <h3></h3>
  - input에 들어있는 텍스트 중에서 '관리' -> '고나리', '확인'->'호가인', '훤하다'->'허누하다'의 방식으로 텍스트를 오타로 바꾸는 이벤트 핸들러 작성하기
  - https://github.com/e-/Hangul.js/blob/master/README.md 에서 라이브러리를 받아서 자음과 모음을 분리하고, 다시 단어로 합치는 기능 살펴보기
  - String.split(''): ''안에 있는 것을 기준으로 문자열을 잘라준다.(return type: 배열)
  - Array.join(''): 배열에 들어 있는 내용들을 하나의                   합치는 것
  - Array.map(function(el)): 배열을 순회하면서 하나의 요소마다 function을 실행시킴 (el: 순회하는 각 요소, return type: 새로운 배열)
    
  1. textarea에 있는 내용물을 가지고 오는 코드
  2. 버튼에 이벤트리스너(click)를 달아주고, 핸들러에는 1번에서 작성한 코드를 넣는다.
  3. 1번 코드의 결과물을 한글자씩 분해해서 배열로 만들어 준다.
  4.  분해한 글자의 4번째 요소가 있는 지 && 2,3 번째 요소가 모음인 경우
  5.  4번의 조건일 때, 3번째, 4번째를  switch하는 것
  6. 결과물로 나온 배열을 문자열로 이어준다.(join)
  7. 결과물을 출력해줄 요소를 찾는다.
  8. 요소에 결과물을 출력한다.
      <script src="./translate.js" type="text/javascript"></script>
      <script type="text/javascript">
      
        $('.translate').on('click', function(){
          var input = $('#input').val();//내용물을 넣거나 가져오는 행위를 한다.
          var result = translate(input);
      
          $('h3').text(result);
          console.log(result);
        })
      
      </script>
  translate.js
      function translate(str){
        //한글자씩 분해가 된다.
        //하나씩 돌아가면서
        return str.split('').map(function(el){
          // el.을 가지고 조작
          var d = Hangul.disassemble(el);
          if(d[3] && Hangul.isVowel(d[1]) && Hangul.isVowel(d[2])){
            var temp = d[2];
            d[2] = d[3];
            d[3] = temp;
          }
          return Hangul.assemble(d);
        }).join('');
      }
  ---
  다른 파일에 있는 것을 불러올 때는 -> Function
  서버에 있는 액션은? -> Ajax
  
  - 클라이언트가 서버로 request할 때에는 Javascript를 보낸다.
  - 서버에서 클라이언트가 response할 때에는 HTML, Js
    - 요청을 보낼 때 필요한 것은 
      - 어느 메소드(액션)으로 보낼 지  -> route
      - 자바스크립트에선 어디로 보낼 것인지만 알면 된다. -> (url,Http Method)
      $.ajax({
          url: 어느 주소로 요청을 보낼지,
          method: 어떤 http method 요청을 보낼 지,
          data: {
          	k: v 어떤 값을 함께 보낼지,
          	// 서버에서는 params[k] => v
      	}
      })
  - http://api.jquery.com/jquery.ajax/
  - https://www.w3schools.com/jquery/ajax_ajax.asp
  - https://opentutorials.org/course/1375/6851



별점

- 유저와 영화의 다대다 관계를 이어주는 테이블

     $ rails g model likes

    class CreateLikes < ActiveRecord::Migration[5.0]
      def change
        create_table :likes do |t|
          t.integer :user_id
          t.integer :movie_id
          t.timestamps
        end
      end
    end

1. 좋아요 버튼을 눌렀을 때
2. 서버에 요청을 보낸다. (현재 유저가 현재 보고있는 이 영화가 좋다고 하는 요청)
3. 서버가 할일
4. 응답이 오면 좋아요 버튼의 텍스트를 좋아요 취소로 바꾸고, btn-info -> btn-warning text-white로 바꿔준다.




