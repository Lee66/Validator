Validator
=========

Form Validator

Init :

<pre>
var F = Validator('form��nameֵ',{
		together : false, //Ĭ���������ϣ���ʾ����������Ϣ,Ĭ��Ϊfalse��ֻ��ʾһ����
		errShow : 'alert', //������ʾ��Ĭ��Ϊalert��֧���ַ���(alert,single,multiple),�Զ���function(string || array())
		errBox : 'error_strings', //������Ϣclass��Ĭ��Ϊform���е� .error_strings
        errPar : 'li', //������Ԫ�صĸ���Ԫ�أ����ڶ�λ�����λ�� li > (span > input ) ~ span.error_strings
		timely : false //ʵʱ�жϣ��Ƿ�ʧȥ�����Լ�change�ж�
});

//�����֤���򣬴���Ϊ��λ����

F.addValidation([
    ["username","required",'��������Ϊ��'],
    ["username","regex=/^[A-Za-z]+$/",'ֻ����a-z'],
    ["username","minlength=3",'�����������3���ַ�'],
    ["username","maxlength=10",'��������С��10���ַ�'],
    ["email","required",'�������'],
    ["email","email",'�����ʽ']
]);

���е���������������function,����

F.addValidation([
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

API :


regex : ���� ��regex=/^[A-Za-z]+$/ ��
required : �������ݣ����input��textarea
minlength : ��С�ַ����� ��minlength=3��
maxlength : ����ַ����� ��maxlength=10��
email : �ʼ���ʽ
telphone : �绰
mobile : �ֻ�
greaterthan : ����ĳ��ֵ������ĳ��input�е�ֵ ��greaterthan=5 ���� greaterthan=�ֶ��� ��
lessthan : С��ĳ��ֵ���÷�ͬ��
equal : ����ĳ��ֵ����������(������|�ָ�)�е�ĳ��ֵ�������ֶ�  ��equal=66 ���� equal=�ֶ��� ����  equal='aa|bb|cc' ��
unequal �� ������ĳ��ֵ���÷�ͬ��

notselect ������ѡ���ֵ��ָ����select��option��value,���� radio/checkbox������ĳһ����value ��notselect=�ַ����������ֻ������飩
shouldselect : ����ѡ�У��÷�ͬ��

minselect : ����ѡ�м���
maxselect : ���ѡ����