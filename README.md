<h1>Validator</h1>
=========

<p>Form Validator</p>

<h2>Init :</h2>

<pre>
var F = Validator('form��nameֵ',{
		together : false, //Ĭ���������ϣ���ʾ����������Ϣ,Ĭ��Ϊfalse��ֻ��ʾһ����
		errShow : 'alert', //������ʾ��Ĭ��Ϊalert��֧���ַ���(alert,single,multiple),�Զ���function(string || array())
		errBox : 'error_strings', //������Ϣclass��Ĭ��Ϊform���е� .error_strings
        errPar : 'li', //������Ԫ�صĸ���Ԫ�أ����ڶ�λ�����λ�� li > (span > input ) ~ span.error_strings
		timely : false //ʵʱ�жϣ��Ƿ�ʧȥ�����Լ�change�ж�
});

//�����֤���򣬴���Ϊ��λ����


F.addRule([
    ["username","required",'��������Ϊ��'],
    ["username","regex=/^[A-Za-z]+$/",'ֻ����a-z'],
    ["username","minlength=3",'�����������3���ַ�'],
    ["username","maxlength=10",'��������С��10���ַ�'],
    ["email","required",'�������'],
    ["email","email",'�����ʽ']
]);

���е���������������function,����

F.addRule([
    ["username","required",function(){ alert('��������Ϊ��') }],
	.....
]);

ȫ�ֵı���Ҳ֧��function(���ղ���Ϊ���������),

errShow : function(data){
    var wrongList = document.getElementById('wrongList'), html = [];
    wrongList.innerHTML = '';
    for(var i =0; i < data.length ; i += 1){
        html.push('<li>'+data[i].msg+'</li>');
    }
    wrongList.innerHTML = html.join('');
}


</pre>

<h2>API :</h2>


regex : ���� ��regex=/^[A-Za-z]+$/ �� <br/>
required : �������ݣ����input��textarea <br/>
minlength : ��С�ַ����� ��minlength=3��<br/>
maxlength : ����ַ����� ��maxlength=10��<br/>
number : ����<br/>
alpha : ��ĸ����Сд���ɣ�<br/>
string : ��ĸ�����֣��»���<br/>
email : �ʼ���ʽ<br/>
telphone : �绰<br/>
mobile : �ֻ�<br/>
greaterthan : ����ĳ��ֵ������ĳ��input�е�ֵ ��greaterthan=5 ���� greaterthan=�ֶ��� ��<br/>
lessthan : С��ĳ��ֵ���÷�ͬ��<br/>
equal : ����ĳ��ֵ����������(������|�ָ�)�е�ĳ��ֵ�������ֶ�  ��equal=66 ���� equal=�ֶ��� ����  equal='aa|bb|cc' ��<br/>
unequal �� ������ĳ��ֵ���÷�ͬ��<br/>

notselect ������ѡ���ֵ��ָ����select��option��value,���� radio/checkbox������ĳһ����value ��notselect=�ַ����������ֻ������飩<br/>
shouldselect : ����ѡ�У��÷�ͬ��<br/>

minselect : ����ѡ�м���<br/>
maxselect : ���ѡ����<br/>