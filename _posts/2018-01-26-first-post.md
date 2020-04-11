---
title: "Welcome to Jekyll!"
date: 2017-10-20 08:26:28 -0400
categories: jekyll update
---


<!DOCTYPE html>

<html>
<head lang="en">
 
	<title></title><meta http_quiv="content-type" content="text/html; charset=utf-8">
    <link rel="stylesheet" href="https://uicdn.toast.com/tui-grid/latest/tui-grid.css" />
    <link rel="stylesheet" type="text/css" href="평가위원_등록_신청서_style.css">
	<script src="https://uicdn.toast.com/tui-grid/latest/tui-grid.js"></script>
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

</head>
<body>

<strong>참석인원 </strong><input type="number" id="myNumber" value="3"><button onclick="confirm()">확인</button>


	<div id="grid"></div>
	
<button onclick="makePrivacyDocu()">개인정보동의서</button>
<button>명패</button>
<button onclick="confirm()">명찰</button>   
  
    
	<script>
        
        window.onload = function() {  

        $("#hiddenDiv").hide();
        
        }
function confirm() {

  var newCount=document.getElementById("myNumber").value;
  var curruntCount=grid.getRowCount();

  if(curruntCount<newCount)
  {
    for(var i=curruntCount;i<newCount;i++)
    {
      grid.appendRow();
    }
  }
  else
  {
      for(var i=newCount;i<curruntCount;i++)
    {
      grid.removeRow(grid.getRowCount()-1);
    }
  }
    
    
    
}
        
        function content_print(){
     
                var initBody = document.body.innerHTML;
                window.onbeforeprint = function(){
                    document.body.innerHTML = document.getElementById('bodyPage').innerHTML;
                }
                window.onafterprint = function(){
                    document.body.innerHTML = initBody;
                }
                window.print();    
            }           
       


출처: https://mkwilson.tistory.com/64 [wilson's story]
        
function makePrivacyDocu()
        {
            $("#bodyPage").empty();
            
            console.log(grid.getRowCount()+"개의 로우임.");
            
            for(var i=0;i<grid.getRowCount();i++)
                {
                     var itm = document.getElementById("privacyDocuSample");
                     var cln = itm.cloneNode(true);
                    document.getElementById("bodyPage").append(cln);
                    document.getElementById("nameInput").innerHTML = "<div id='nameInput"+i+"'>"+grid.getValue(i, "name")+"</div>";
                    document.getElementById("nameInput2").innerHTML = "<div id='nameInput2"+i+"'>"+grid.getValue(i, "name")+"</div>";                    
                    document.getElementById("dutyInput").innerHTML = "<div id='dutyInput"+i+"'>"+grid.getValue(i, "duty")+"</div>";
                    document.getElementById("companyInput").innerHTML = "<div id='companyInput"+i+"'>"+grid.getValue(i, "company")+"</div>";
                    document.getElementById("dateInput").innerHTML = "<div id='dateInput"+i+"'>"+grid.getValue(i, "date")+"</div>";
                     $("#bodyPage").show();
                }
            
            var popupWindow = window.open("", "_blank" );
           popupWindow.document.write( "<head>"); //head 제대로 쓰니까..티스토리 에러가...
popupWindow.document.write( $('head').html() );
           popupWindow.document.write( "</head>"); //head 제대로 쓰니까..티스토리 에러가...

 
popupWindow.document.write( '<body>' );
popupWindow.document.write( '<div>' );
popupWindow.document.write( document.getElementById("bodyPage").innerHTML);
popupWindow.document.write( '</div></body>' );
popupWindow.document.close();

            
            console.log(document.getElementById("bodyPage").innerHTML);
            
            //content_print();
        }

function myFunction() {
  var x = document.getElementById("myBtn1");
  x.disabled = true;
}

const gridData = [
      {
        company: '화남초등학교',
        name: '이정서',
        duty: '교사',
        date: '2020.12.26',
        event: '20년 sw교육 선도학교 최종평가',
        pay: '200000',
        transport: '80000',
        paysum: '280000',
      },
      {
        company: '서울시교육청',
        name: '김유신',
        duty: '장학사',
        date: '2020.12.26',
        event: '20년 sw교육 선도학교 최종평가',
        pay: '200000',
        transport: '20000',
        paysum: '220000',
      },
      {
        company: '창건건축사무소',
        name: '김건축',
        duty: '건축사',
        date: '2020.12.26',
        event: '20년 sw교육 선도학교 최종평가',
        pay: '200000',
        transport: '50000',
        paysum: '250000',
      }
    ];

      class CustomTextEditor {
      constructor(props) {
        const el = document.createElement('input');
        const { maxLength } = props.columnInfo.editor.options;

        el.type = 'text';
        el.maxLength = maxLength;
        el.value = String(props.value);

        this.el = el;
      }

      getElement() {
        return this.el;
      }

      getValue() {
        return this.el.value;
      }

      mounted() {
        this.el.select();
      }
    }

    const grid = new tui.Grid({
      el: document.getElementById('grid'),
      scrollX: false,
      scrollY: false,
      rowHeaders: ['rowNum'],
      columns: [
        {
          header: 'Company',
          name: 'company',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'center'
        },
        {
          header: 'Name',
          name: 'name',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'center'
        },
           {
          header: 'Duty',
          name: 'duty',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'center'
        },
        {
          header: 'Date',
          name: 'date',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'center'
        },
        {
          header: 'Event',
          name: 'event',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'center'
        },
        {
          header: 'Pay',
          name: 'pay',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'right'
        },
        {
          header: 'Transport',
          name: 'transport',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'right'
        },
        {
          header: 'Paysum',
          name: 'paysum',
          onBeforeChange(ev) {
            console.log('Before change:' + ev);
           
          },
          onAfterChange(ev) {
            console.log('After change:' + ev);
          },
          editor: 'text',
          align: 'right'
        }
      ],
      columnOptions: {
        resizable: true
      }
    });

   grid.resetData(gridData);
	</script>
    <div id=bodyPage>
    
    </div>    
    <div id=hiddenDiv>
    <div id=privacyDocuSample>
        <div class="hpa" style="width:210mm;height:297mm;"><div class="hcD" style="left:20mm;top:15mm;"><div class="hcI"><div class="hls ps3" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:170mm;"></div></div></div><div class="hcD" style="left:20mm;top:24.99mm;"><div class="hcI"><div class="hls ps0" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:0mm;"></div></div></div><div class="htb" style="left:20.49mm;width:172.24mm;top:25.49mm;height:244.80mm;"><svg class="hs" viewBox="-2.50 -2.50 177.24 249.79" style="left:-2.50mm;top:-2.50mm;width:177.24mm;height:249.79mm;"><defs><pattern id="w_00" width="10" height="10" patternUnits="userSpaceOnUse"><rect width="10" height="10" fill="rgb(204,204,204)"/></pattern></defs><path fill="url(#w_00)" d="M0,0L171.26,0L171.26,7.63L0,7.63L0,0Z "></path><defs><pattern id="w_01" width="10" height="10" patternUnits="userSpaceOnUse"><rect width="10" height="10" fill="rgb(229,229,229)"/></pattern></defs><path fill="url(#w_01)" d="M0,7.63L25.02,7.63L25.02,21.39L0,21.39L0,7.63Z "></path><path fill="url(#w_01)" d="M67.34,7.63L81.63,7.63L81.63,21.39L67.34,21.39L67.34,7.63Z "></path><path fill="url(#w_01)" d="M112.46,7.63L131.41,7.63L131.41,21.39L112.46,21.39L112.46,7.63Z "></path><path fill="url(#w_01)" d="M0,21.39L25.02,21.39L25.02,33.36L0,33.36L0,21.39Z "></path><path fill="url(#w_01)" d="M112.46,21.39L131.41,21.39L131.41,33.36L112.46,33.36L112.46,21.39Z "></path><path fill="url(#w_01)" d="M0,33.36L25.02,33.36L25.02,45.68L0,45.68L0,33.36Z "></path><path fill="url(#w_01)" d="M0,45.68L25.02,45.68L25.02,57L0,57L0,45.68Z "></path><path fill="url(#w_01)" d="M89.70,45.68L108.88,45.68L108.88,57L89.70,57L89.70,45.68Z "></path><path fill="url(#w_01)" d="M0,57L25.02,57L25.02,96.03L0,96.03L0,57Z "></path><path fill="url(#w_01)" d="M0,96.03L25.02,96.03L25.02,132.07L0,132.07L0,96.03Z "></path><defs><pattern id="w_02" width="10" height="10" patternUnits="userSpaceOnUse"><rect width="10" height="10" fill="rgb(242,242,242)"/></pattern></defs><path fill="url(#w_02)" d="M25.02,96.03L46.66,96.03L46.66,115.30L25.02,115.30L25.02,96.03Z "></path><path fill="url(#w_02)" d="M46.66,96.03L63.71,96.03L63.71,106.72L46.66,106.72L46.66,96.03Z "></path><path fill="url(#w_02)" d="M63.71,96.03L80.76,96.03L80.76,106.72L63.71,106.72L63.71,96.03Z "></path><path fill="url(#w_02)" d="M80.76,96.03L94.82,96.03L94.82,106.72L80.76,106.72L80.76,96.03Z "></path><path fill="url(#w_02)" d="M94.82,96.03L108.88,96.03L108.88,106.72L94.82,106.72L94.82,96.03Z "></path><path fill="url(#w_02)" d="M108.88,96.03L125.93,96.03L125.93,106.72L108.88,106.72L108.88,96.03Z "></path><path fill="url(#w_02)" d="M125.93,96.03L142.99,96.03L142.99,106.72L125.93,106.72L125.93,96.03Z "></path><path fill="url(#w_02)" d="M142.99,96.03L157.05,96.03L157.05,106.72L142.99,106.72L142.99,96.03Z "></path><path fill="url(#w_02)" d="M157.05,96.03L171.26,96.03L171.26,106.72L157.05,106.72L157.05,96.03Z "></path><path fill="url(#w_02)" d="M25.02,115.30L46.66,115.30L46.66,132.07L25.02,132.07L25.02,115.30Z "></path><path fill="url(#w_02)" d="M46.66,115.30L63.71,115.30L63.71,124L46.66,124L46.66,115.30Z "></path><path fill="url(#w_02)" d="M63.71,115.30L80.76,115.30L80.76,124L63.71,124L63.71,115.30Z "></path><path fill="url(#w_02)" d="M80.76,115.30L94.82,115.30L94.82,124L80.76,124L80.76,115.30Z "></path><path fill="url(#w_02)" d="M94.82,115.30L108.88,115.30L108.88,124L94.82,124L94.82,115.30Z "></path><path fill="url(#w_02)" d="M108.88,115.30L125.93,115.30L125.93,124L108.88,124L108.88,115.30Z "></path><path fill="url(#w_02)" d="M125.93,115.30L142.99,115.30L142.99,124L125.93,124L125.93,115.30Z "></path><path fill="url(#w_02)" d="M142.99,115.30L171.26,115.30L171.26,124L142.99,124L142.99,115.30Z "></path><path fill="url(#w_01)" d="M0,132.07L25.02,132.07L25.02,153.91L0,153.91L0,132.07Z "></path><defs><pattern id="w_03" width="10" height="10" patternUnits="userSpaceOnUse"><rect width="10" height="10" fill="rgb(206,222,239)"/></pattern></defs><path fill="url(#w_03)" d="M0,153.91L25.02,153.91L25.02,160.43L0,160.43L0,153.91Z "></path><defs><pattern id="w_04" width="10" height="10" patternUnits="userSpaceOnUse"><rect width="10" height="10" fill="rgb(230,238,247)"/></pattern></defs><path fill="url(#w_04)" d="M25.02,153.91L171.26,153.91L171.26,160.43L25.02,160.43L25.02,153.91Z "></path><path fill="url(#w_03)" d="M0,160.43L25.02,160.43L25.02,173.29L0,173.29L0,160.43Z "></path><path fill="url(#w_04)" d="M25.02,160.43L171.26,160.43L171.26,173.29L25.02,173.29L25.02,160.43Z "></path><path fill="url(#w_03)" d="M0,173.29L25.02,173.29L25.02,179.80L0,179.80L0,173.29Z "></path><path fill="url(#w_04)" d="M25.02,173.29L171.26,173.29L171.26,179.80L25.02,179.80L25.02,173.29Z "></path><defs><pattern id="w_05" width="10" height="10" patternUnits="userSpaceOnUse"><rect width="10" height="10" fill="rgb(255,255,255)"/></pattern></defs><path fill="url(#w_05)" d="M0,179.80L171.26,179.80L171.26,196.47L0,196.47L0,179.80Z "></path><path d="M0,0 L0,96.03" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M0,96.03 L0,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M0,132.07 L0,153.92" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M0,153.91 L0,196.48" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M0,196.47 L0,243.81" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M25.02,7.63 L25.02,179.80" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M46.66,96.03 L46.66,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M63.71,96.03 L63.71,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M67.34,7.63 L67.34,21.39" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M80.76,96.03 L80.76,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M81.63,7.63 L81.63,21.39" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M89.70,45.68 L89.70,57.01" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M94.82,96.03 L94.82,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M108.88,45.68 L108.88,57.01" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M108.88,96.03 L108.88,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M112.46,7.63 L112.46,33.37" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M125.93,96.03 L125.93,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M131.41,7.63 L131.41,33.37" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M142.99,96.03 L142.99,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M157.05,96.03 L157.05,115.31" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M171.26,0 L171.26,96.03" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M171.26,96.03 L171.26,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M171.26,132.07 L171.26,153.92" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M171.26,153.91 L171.26,196.48" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M171.26,196.47 L171.26,243.81" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M39.27,57 L39.27,82.53" style="stroke:#000000;stroke-linecap:butt;stroke-dasharray:0.17,0.26;stroke-width:0.12;"></path><path d="M-0.06,0 L171.32,0" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.06,7.63 L171.32,7.63" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.06,21.39 L171.32,21.39" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.06,33.36 L171.32,33.36" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.06,45.68 L171.32,45.68" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.06,57 L171.32,57" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.06,96.03 L171.51,96.03" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M46.60,106.72 L171.51,106.72" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M24.97,115.30 L171.51,115.30" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M46.60,124 L171.51,124" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.25,132.07 L171.51,132.07" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M-0.06,153.91 L171.51,153.91" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M-0.25,160.43 L171.51,160.43" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.25,173.29 L171.51,173.29" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.25,179.80 L171.51,179.80" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M-0.25,196.47 L171.51,196.47" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M-0.06,243.81 L171.32,243.81" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M24.97,65.51 L171.32,65.51" style="stroke:#000000;stroke-linecap:butt;stroke-dasharray:0.17,0.26;stroke-width:0.12;"></path><path d="M24.97,74.02 L171.32,74.02" style="stroke:#000000;stroke-linecap:butt;stroke-dasharray:0.17,0.26;stroke-width:0.12;"></path><path d="M24.97,82.53 L171.32,82.53" style="stroke:#000000;stroke-linecap:butt;stroke-dasharray:0.17,0.26;stroke-width:0.12;"></path><path d="M39.27,57 L39.27,82.53" style="stroke:#000000;stroke-linecap:butt;stroke-dasharray:0.17,0.26;stroke-width:0.12;"></path><path d="M0,196.47 L0,243.81" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M0,153.91 L0,196.48" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M0,132.07 L0,153.92" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M0,96.03 L0,132.08" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.50;"></path><path d="M0,0 L0,96.03" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path><path d="M24.97,82.53 L171.32,82.53" style="stroke:#000000;stroke-linecap:butt;stroke-dasharray:0.17,0.26;stroke-width:0.12;"></path><path d="M-0.06,0 L171.32,0" style="stroke:#000000;stroke-linecap:butt;stroke-width:0.12;"></path></svg><div class="hce" style="left:0mm;top:0mm;width:171.26mm;height:7.63mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.85mm;"><div class="hls ps12" style="line-height:4.10mm;white-space:nowrap;left:0mm;top:-0.25mm;height:4.94mm;width:170.26mm;"><span class="hrt cs26">평가위원 등록 신청서</span></div></div></div></div><div class="hce" style="left:0mm;top:7.63mm;width:25.02mm;height:13.76mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.80mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">성명</span></div></div></div></div><div class="hce" style="left:25.02mm;top:7.63mm;width:42.32mm;height:13.76mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.80mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:41.32mm;"><span class="hrt cs14" id="nameInput">이름 넣는 곳</span></div></div></div></div><div class="hce" style="left:67.34mm;top:7.63mm;width:14.29mm;height:13.76mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.80mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.31mm;"><span class="hrt cs14">성별</span></div></div></div></div><div class="hce" style="left:81.63mm;top:7.63mm;width:30.83mm;height:13.76mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.80mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:29.83mm;"><span class="hrt cs12">(남 ‖ 여)</span></div></div></div></div><div class="hce" style="left:112.46mm;top:7.63mm;width:18.95mm;height:13.76mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.80mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:17.95mm;"><span class="hrt cs14">주민번호</span></div></div></div></div><div class="hce" style="left:131.41mm;top:7.63mm;width:39.85mm;height:13.76mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI"><div class="hls ps12" style="line-height:2.17mm;white-space:nowrap;left:0mm;top:-0.14mm;height:2.82mm;width:38.85mm;"><span class="hrt cs10">※수당지급 시 필요</span></div><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:4.36mm;height:3.17mm;width:38.85mm;"></div><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:9.44mm;height:3.17mm;width:38.85mm;"></div></div></div></div><div class="hce" style="left:0mm;top:21.39mm;width:25.02mm;height:11.97mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.91mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">소속</span></div></div></div></div><div class="hce" style="left:25.02mm;top:21.39mm;width:87.44mm;height:11.97mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.54mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:86.44mm;"><span class="hrt cs14" id="companyInput">소속 넣는 곳</span></div><div class="hls ps12" style="line-height:2.17mm;white-space:nowrap;left:0mm;top:4.94mm;height:2.82mm;width:86.44mm;"><span class="hrt cs10">※소속이 변경되는 경우, 한국과학창의재단 담당자에게 전달&nbsp;</span></div></div></div></div><div class="hce" style="left:112.46mm;top:21.39mm;width:18.95mm;height:11.97mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.91mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:17.95mm;"><span class="hrt cs14">직위</span></div></div></div></div><div class="hce" style="left:131.41mm;top:21.39mm;width:39.85mm;height:11.97mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.91mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:38.85mm;"><span class="hrt cs14" id="dutyInput">직위 넣는 곳</span></div></div></div></div><div class="hce" style="left:0mm;top:33.36mm;width:25.02mm;height:12.32mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.01mm;"><div class="hls ps13" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">주소</span></div><div class="hls ps13" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">(근무지)</span></div></div></div></div><div class="hce" style="left:25.02mm;top:33.36mm;width:146.23mm;height:12.32mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.08mm;"><div class="hls ps15" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:145.25mm;"><span class="hrt cs12">&nbsp;</span></div></div></div></div><div class="hce" style="left:0mm;top:45.68mm;width:25.02mm;height:11.32mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.58mm;"><div class="hls ps13" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">휴대폰</span></div></div></div></div><div class="hce" style="left:25.02mm;top:45.68mm;width:64.67mm;height:11.32mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.58mm;"><div class="hls ps15" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:63.68mm;"></div></div></div></div><div class="hce" style="left:89.70mm;top:45.68mm;width:19.18mm;height:11.32mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.58mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:18.19mm;"><span class="hrt cs14">이메일</span></div></div></div></div><div class="hce" style="left:108.88mm;top:45.68mm;width:62.37mm;height:11.32mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:3.58mm;"><div class="hls ps15" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:61.38mm;"></div></div></div></div><div class="hce" style="left:0mm;top:57mm;width:25.02mm;height:39.03mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:17.43mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">전공</span></div></div></div></div><div class="hce" style="left:25.02mm;top:57mm;width:14.25mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.25mm;"><span class="hrt cs12">&nbsp;</span><span class="hrt cs14">[학사]</span><span class="hrt cs12">&nbsp;</span></div></div></div></div><div class="hce" style="left:39.27mm;top:57mm;width:49.19mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:48.19mm;"></div></div></div></div><div class="hce" style="left:88.46mm;top:57mm;width:24.36mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:23.37mm;"><span class="hrt cs12">&nbsp;&nbsp;&nbsp;대학교(원)&nbsp;</span></div></div></div></div><div class="hce" style="left:112.81mm;top:57mm;width:40.20mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:39.21mm;"></div></div></div></div><div class="hce" style="left:153.02mm;top:57mm;width:18.24mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:17.24mm;"><span class="hrt cs12">&nbsp;&nbsp;학과</span></div></div></div></div><div class="hce" style="left:25.02mm;top:65.51mm;width:14.25mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.25mm;"><span class="hrt cs14">&nbsp;[석사]</span><span class="hrt cs12">&nbsp;</span></div></div></div></div><div class="hce" style="left:39.27mm;top:65.51mm;width:49.19mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:48.19mm;"></div></div></div></div><div class="hce" style="left:88.46mm;top:65.51mm;width:24.36mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:23.37mm;"><span class="hrt cs12">&nbsp;&nbsp;&nbsp;대학교(원)</span></div></div></div></div><div class="hce" style="left:112.81mm;top:65.51mm;width:40.20mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:39.21mm;"></div></div></div></div><div class="hce" style="left:153.02mm;top:65.51mm;width:18.24mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:17.24mm;"><span class="hrt cs12">&nbsp;&nbsp;학과</span></div></div></div></div><div class="hce" style="left:25.02mm;top:74.02mm;width:14.25mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.25mm;"><span class="hrt cs12">&nbsp;</span><span class="hrt cs14">[박사]</span><span class="hrt cs12">&nbsp;</span></div></div></div></div><div class="hce" style="left:39.27mm;top:74.02mm;width:49.19mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:48.19mm;"></div></div></div></div><div class="hce" style="left:88.46mm;top:74.02mm;width:24.36mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:23.37mm;"><span class="hrt cs12">&nbsp;&nbsp;&nbsp;대학교(원)</span></div></div></div></div><div class="hce" style="left:112.81mm;top:74.02mm;width:40.20mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:39.21mm;"></div></div></div></div><div class="hce" style="left:153.02mm;top:74.02mm;width:18.24mm;height:8.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.17mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:17.24mm;"><span class="hrt cs12">&nbsp;&nbsp;학과&nbsp;</span></div></div></div></div><div class="hce" style="left:25.02mm;top:82.53mm;width:146.23mm;height:13.50mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.49mm;"><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:145.25mm;"><span class="hrt cs15">※추가 학위 기재&nbsp;</span></div><div class="hls ps20" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:6.19mm;height:3.17mm;width:145.25mm;"></div></div></div></div><div class="hce" style="left:0mm;top:96.03mm;width:25.02mm;height:36.04mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:10.86mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">평가분야</span></div><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:4.92mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">(‘O’표시)</span></div><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:10mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">*중복선택가능</span></div></div></div></div><div class="hce" style="left:25.02mm;top:96.03mm;width:21.64mm;height:19.27mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:5.49mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:20.64mm;"><span class="hrt cs16">공통분야</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:20.64mm;"><span class="hrt cs17">(입찰용역 등)</span></div></div></div></div><div class="hce" style="left:46.66mm;top:96.03mm;width:17.05mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">행사</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">운영</span></div></div></div></div><div class="hce" style="left:63.71mm;top:96.03mm;width:17.05mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">국내외</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">연수</span></div></div></div></div><div class="hce" style="left:80.76mm;top:96.03mm;width:14.06mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">홍보·</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">마케팅</span></div></div></div></div><div class="hce" style="left:94.82mm;top:96.03mm;width:14.06mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">전시·</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">디자인</span></div></div></div></div><div class="hce" style="left:108.88mm;top:96.03mm;width:17.05mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">콘텐츠</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">개발</span></div></div></div></div><div class="hce" style="left:125.93mm;top:96.03mm;width:17.05mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">시스템</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">구축</span></div></div></div></div><div class="hce" style="left:142.99mm;top:96.03mm;width:14.06mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">경영</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">관리</span></div></div></div></div><div class="hce" style="left:157.05mm;top:96.03mm;width:14.21mm;height:10.69mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.22mm;"><span class="hrt cs16">기타</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:13.22mm;"><span class="hrt cs20">(직접기재)</span></div></div></div></div><div class="hce" style="left:46.66mm;top:106.72mm;width:17.05mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:63.71mm;top:106.72mm;width:17.05mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:80.76mm;top:106.72mm;width:14.06mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"></div></div></div></div><div class="hce" style="left:94.82mm;top:106.72mm;width:14.06mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"></div></div></div></div><div class="hce" style="left:108.88mm;top:106.72mm;width:17.05mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:125.93mm;top:106.72mm;width:17.05mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:142.99mm;top:106.72mm;width:14.06mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"></div></div></div></div><div class="hce" style="left:157.05mm;top:106.72mm;width:14.21mm;height:8.58mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.21mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.22mm;"></div></div></div></div><div class="hce" style="left:25.02mm;top:115.30mm;width:21.64mm;height:16.77mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.24mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:20.64mm;"><span class="hrt cs16">전문분야</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:20.64mm;"><span class="hrt cs17">(정책연구 등)</span></div></div></div></div><div class="hce" style="left:46.66mm;top:115.30mm;width:17.05mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">SW</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">교육</span></div></div></div></div><div class="hce" style="left:63.71mm;top:115.30mm;width:17.05mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">과학</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">교육</span></div></div></div></div><div class="hce" style="left:80.76mm;top:115.30mm;width:14.06mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">수학</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">교육</span></div></div></div></div><div class="hce" style="left:94.82mm;top:115.30mm;width:14.06mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">융합</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:13.07mm;"><span class="hrt cs16">교육</span></div></div></div></div><div class="hce" style="left:108.88mm;top:115.30mm;width:17.05mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">교육</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">기부</span></div></div></div></div><div class="hce" style="left:125.93mm;top:115.30mm;width:17.05mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">과학기술</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:16.06mm;"><span class="hrt cs16">과학문화</span></div></div></div></div><div class="hce" style="left:142.99mm;top:115.30mm;width:28.27mm;height:8.70mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:0.20mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:27.28mm;"><span class="hrt cs16">기타</span></div><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:3.98mm;height:3.17mm;width:27.28mm;"><span class="hrt cs16">(직접기재)</span></div></div></div></div><div class="hce" style="left:46.66mm;top:124mm;width:17.05mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:63.71mm;top:124mm;width:17.05mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:80.76mm;top:124mm;width:14.06mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"></div></div></div></div><div class="hce" style="left:94.82mm;top:124mm;width:14.06mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:13.07mm;"></div></div></div></div><div class="hce" style="left:108.88mm;top:124mm;width:17.05mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:125.93mm;top:124mm;width:17.05mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:16.06mm;"></div></div></div></div><div class="hce" style="left:142.99mm;top:124mm;width:28.27mm;height:8.08mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1.95mm;"><div class="hls ps16" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:27.28mm;"></div></div></div></div><div class="hce" style="left:0mm;top:132.07mm;width:25.02mm;height:21.84mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:6.30mm;"><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">재단참여&nbsp;</span></div><div class="hls ps12" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:4.92mm;height:3.17mm;width:24.03mm;"><span class="hrt cs14">(평가경험)</span></div></div></div></div><div class="hce" style="left:25.02mm;top:132.07mm;width:146.23mm;height:21.84mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:8.84mm;"><div class="hls ps14" style="line-height:2.48mm;white-space:nowrap;left:0mm;top:-0.16mm;height:3.17mm;width:145.25mm;"></div></div></div></div><div class="hce" style="left:0mm;top:153.91mm;width:25.02mm;height:6.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1mm;"><div class="hls ps28" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:24.03mm;"><span class="hrt cs9">수집·이용 목적</span></div></div></div></div><div class="hce" style="left:25.02mm;top:153.91mm;width:146.23mm;height:6.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1mm;"><div class="hls ps0" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:145.25mm;"><span class="hrt cs0">&nbsp;한국과학창의재단 사업수행 관련 사업자 선정 등을 위한 평가위원 등록&nbsp;</span></div></div></div></div><div class="hce" style="left:0mm;top:160.43mm;width:25.02mm;height:12.86mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:4.17mm;"><div class="hls ps28" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:24.03mm;"><span class="hrt cs9">수집 항목</span></div></div></div></div><div class="hce" style="left:25.02mm;top:160.43mm;width:146.23mm;height:12.86mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1mm;"><div class="hls ps26" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:145.25mm;"><span class="hrt cs8">&nbsp;</span><span class="hrt cs21">소득세법 제145조(기타소득에 대한 원천징수시기와 방법 및 원천징수영수증의 발급)에 의거</span></div><div class="hls ps26" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:6.17mm;height:3.53mm;width:145.25mm;"><span class="hrt cs21">&nbsp;하여 아래와 같이 개인정보(이름, 주소, 소속기관, 연락처, 이메일,&nbsp;</span><span class="hrt cs23">주민</span><span class="hrt cs25">번호)</span><span class="hrt cs21">를 수집합니다.</span></div></div></div></div><div class="hce" style="left:0mm;top:173.29mm;width:25.02mm;height:6.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1mm;"><div class="hls ps28" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:24.03mm;"><span class="hrt cs22">보유 및 이용기간</span></div></div></div></div><div class="hce" style="left:25.02mm;top:173.29mm;width:146.23mm;height:6.51mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1mm;"><div class="hls ps26" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:145.25mm;"><span class="hrt cs8">&nbsp;</span><span class="hrt cs13">국세기본법 제85조의3(장부 등의 비치와 보존)에 의거 해당 국세의 법정신고기한이 지난날부터&nbsp;</span><span class="hrt cs24">5년</span></div></div></div></div><div class="hce" style="left:0mm;top:179.80mm;width:171.26mm;height:16.67mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:1mm;"><div class="hls ps27" style="line-height:2.79mm;white-space:nowrap;left:5.29mm;top:-0.18mm;height:3.53mm;width:164.97mm;"><span class="hrt cs9">위와 같이 개인정보를 수집·활용하는데 동의하십니까?</span></div><div class="hls ps27" style="line-height:1.59mm;white-space:nowrap;left:5.29mm;top:6.24mm;height:2.12mm;width:164.97mm;"></div><div class="hls ps27" style="line-height:2.79mm;white-space:nowrap;left:5.29mm;top:9.98mm;height:3.53mm;width:164.97mm;"><span class="hrt cs9">□ 동의함 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;□ 동의하지 않음</span></div></div></div></div><div class="hce" style="left:0mm;top:196.47mm;width:171.26mm;height:47.34mm;"><div class="hcD" style="left:0.49mm;top:0.49mm;"><div class="hcI" style="top:2.64mm;"><div class="hls ps28" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:-0.18mm;height:3.53mm;width:170.26mm;"><span class="hrt cs8">개인정보 수집·이용목적, 수집항목, 보유 및 이용기간, 동의를 거부할 권리가 있다는 사실을&nbsp;</span></div><div class="hls ps28" style="line-height:2.79mm;white-space:nowrap;left:0mm;top:6.17mm;height:3.53mm;width:170.26mm;"><span class="hrt cs8">안내 받았으며, 평가위원 등록 신청을 위해 개인정보 수집·활용하는 것에 동의합니다.</span></div><div class="hls ps17" style="line-height:1.59mm;white-space:nowrap;left:3.53mm;top:12.59mm;height:2.12mm;width:163.21mm;"></div><div class="hls ps18" style="line-height:2.79mm;white-space:nowrap;left:3.53mm;top:16.33mm;height:3.53mm;width:163.21mm;"><span class="hrt cs8"><span class="hrt cs14" id="dateInput">날짜 넣는 곳</span></span></div><div class="hls ps18" style="line-height:1.59mm;white-space:nowrap;left:3.53mm;top:22.75mm;height:2.12mm;width:163.21mm;"></div><div class="hls ps19" style="line-height:2.79mm;white-space:nowrap;left:3.53mm;top:26.49mm;height:3.53mm;width:157.15mm;"><span class="hrt cs8">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;신청인 : &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hrt cs14" id="nameInput2">이름 넣는 곳</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(인)</span></div><div class="hls ps19" style="line-height:1.59mm;white-space:nowrap;left:3.53mm;top:32.91mm;height:2.12mm;width:157.15mm;"></div><div class="hls ps25" style="line-height:3.43mm;white-space:nowrap;left:3.53mm;top:36.62mm;height:4.23mm;width:157.15mm;"><span class="hrt cs11">한국과학창의재단 이사장 귀하</span></div></div></div></div></div></div><div></divdiv>
    </div>
</body>
</html>
