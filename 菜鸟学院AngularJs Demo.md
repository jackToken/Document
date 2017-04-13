###AngularJs笔记
	<script src="js/angular.min.js"></script>
	ng-app: define application
	ng-controller: define controller
	ng-init: module init
	ng-model: model
	ng-bind: bind as innerHTML
	ng-show: require show error info
	ng-click: click event
	{{bind_name}}: output ng-model params
	{{myForm.userEmail.$valid}}
	{{myForm.userEmail.$dirty}}
	{{myForm.userEmail.$touched}}
####Examples
#####example 1.
	<body>
		<div ng-app="myApp" ng-controller="myController">
			<p><input type="text" ng-model="username"/></p>
			<p><input type="age" ng-model="age"></p>
			<p><span ng-bind="username"></span></p>
			<p><span ng-bind="age"></span></p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var myApp = angular.module('myApp', []);
		myApp.controller('myController', function($scope){
			$scope.username="join";
			$scope.age="18"
		});
	</script>
#####example 2.
	<body>
		<!--
		<div ng-app="myApp" ng-controller="myController" ng-init="numbers=5;price=20">
			<p>numbers:<input type="text" ng-model="numbers"></p>
			<p>price:<input type="text" ng-model="price"></p>
			<p>money:{{numbers * price}}</p>
		</div>
		-->
		<div ng-app="appName" ng-controller="appController" ng-init="username1='jack';username2='tom'">
			<p>Names:{{username1 + " " + username2}}</p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<!--
	<script type="text/javascript">
		var myApp = angular.module('myApp', []);
		myApp.controller('myController', function($scope){
			$scope.numbers = 10;
			$scope.price = 2;
		});
	</script>
	-->
	<script type="text/javascript">
		var appName = angular.module('appName', []);
		appName.controller('appController', function($scope) {
			
		});
	</script>
#####example 3.
	<body>
		<!--
		<div ng-app="appName" ng-controller="appController" ng-init="person={username:'jack',age:18}">
			<p>Name:{{person.username}}</p>
			<p>Age:<span ng-bind="person.age"></span></p>
		</div>
		<div ng-app="" ng-init="person=[1,2,3,4,5]">
			<p>Array Item:{{ person[0] }}</p>
		</div>
		-->
		<div ng-app="" ng-init="person={1,2,3,4,5}">
			<p>Array Item:{{person[0]}}</p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var myApp = angular.module('appName', []);
		myApp.controller('appController', function($scope) {
			
		});
	</script>
#####example 4.
	<body>
		<!--
		<div ng-app="" ng-init="persons=['jack','tom','google']">
			<ul>
				<li ng-repeat="x in persons">
					{{x}}
				</li>
			</ul>
		</div>
		-->
		<div ng-app="" ng-init="names=[{name:'Jani',country:'Norway'},
		{name:'Hege',country:'Sweden'},{name:'Kai',country:'Denmark'}]">
			<ul>
				<li ng-repeat="item in names">
					{{item.name + " " + item.country}}
				</li>
			</ul>	
		</div>
	</body>
	<script src="js/angular.min.js"></script>
#####example 5.
	<!--
	<body ng-app="appName">
		<username></username>
	</body>
	<script type="text/javascript">
		var appName = angular.module('appName', []);
		appName.directive("username", function() {
			return {
				template : "<h1>自定义指令!</h1>"
			};
		});
	</script>
	-->
	<body ng-app="appName">
		<div user-name></div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var appName = angular.module('appName', []);
		appName.directive('userName', function(){
			return {
				restrict:'A',
				template:'<h1>UserName</h1>'
			};
		});
	</script>
#####example 6.
	<body>
		<form ng-app="ngApp" ng-controller="ngController" name="formName">
			Email:<input type="email" ng-model="emailName" name="emailName"/>
			<span ng-show="formName.emailName.$error.email">Please input email.</span>
		</form>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.emailName = 'email@163.com';
		});
	</script>
#####example 7.
	<body>
		<form name="myForm" ng-app="myApp" ng-controller="myController">
			<p>
				Email:<input type="email" name="userEmail" ng-model="userEmail">
				<span ng-show="myForm.userEmail.$error.email">Please input email.</span>
			</p>
			<p>
				<h1>状态</h1><br>
				valid:{{myForm.userEmail.$valid}}<br>
				dirty:{{myForm.userEmail.$dirty}}<br>
				touched:{{myForm.userEmail.$touched}}
			</p>
		</form>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var myApp = angular.module('myApp', []);
		myApp.controller('myController', function($scope){
			$scope.userEmail = 'user@163.com';
		});
	</script>
#####example 8.
	<style type="text/css">
		input.ng-invalid {
			background-color:lightblue;
		}
	</style>
	<body>
		<form name="formName" ng-app="ngApp" ng-controller="ngController">
			<p>
				Email <input type="email" ng-model="userEmail" name="userEmail"/>
			</p>
		</form>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.userEmail = 'user@163.com';
		});
	</script>

	ng-model 指令基于它们的状态为 HTML 元素提供了 CSS 类：
	    ng-empty
	    ng-not-empty
	    ng-touched
	    ng-untouched
	    ng-valid
	    ng-invalid
	    ng-dirty
	    ng-pending
	    ng-pristine
#####example 9.
	<body>
		<form name="ngForm" ng-app="ngApp" ng-controller="ngController">
			<h1>{{greeting}}</h1>
			<p>
				UserName <input type="text" ng-model="userName" name="userName"/><br>
				<button ng-click="sayHello()">Click</button>
			</p>
		</form>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.userName = 'UserName';
			$scope.sayHello = function() {
				$scope.greeting = "Hello " + $scope.userName;	
			};
		});
	</script>
#####example 10.
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			{{sayHello()}}
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.sayHello = function() {
				return "firstname1";
			};
		});
	</script>
#####example 11.
	1、uppercase，lowercase 大小写转换
		{{ "lower cap string" | uppercase }}   // 结果：LOWER CAP STRING
		{{ "TANK is GOOD" | lowercase }}      // 结果：tank is good	
	2、date 格式化
		{{1490161945000 | date:"yyyy-MM-dd HH:mm:ss"}} // 2017-03-22 13:52:25	
	3、number 格式化（保留小数）
		{{149016.1945000 | number:2}}
	4、currency货币格式化	
		{{ 250 | currency }}            // 结果：$250.00
		{{ 250 | currency:"RMB ￥ " }}  // 结果：RMB ￥ 250.00

	AngularJs过滤器
		currency 	格式化数字为货币格式
		filter 	从数组项中选择一个子集
		lowercase 	格式化字符串为小写
		orderBy 	根据某个表达式排列数组
		uppercase 	格式化字符串为大写
	<body>
		<!--
		<div ng-app="ngApp" ng-controller="ngController">
			{{firstName | uppercase}}
		</div>
		<div ng-app="ngApp" ng-controller="ngController">
			{{firstName | lowercase}}
		</div>
		<div ng-app="ngApp" ng-controller="ngController">
			{{number * price | currency}}
		</div>
		-->
		<div ng-app="ngApp" ng-controller="ngController">
			<ul>
				<li ng-repeat="item in person | orderBy:'number'">
					{{item.number + " " + item.content}}
				</li>
			</ul>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope) {
			//$scope.firstName = 'abc';
			//$scope.firstName = 'ABC';
			//$scope.number = 10;
			//$scope.price = 2;
			$scope.person = [{number:3,content:333}, 
			{number:2,content:222}, {number:1,content:111}];
		});
	</script>
#####example 12.
	1、filter查找
		输入过滤器可以通过一个管道字符（|）和一个过滤器添加到指令中，该过滤器后跟一个冒号和一个模型名称。
		
		filter 过滤器从数组中选择一个子集
		
		 // 查找name为iphone的行
		{{ [{"age": 20,"id": 10,"name": "iphone"},
		{"age": 12,"id": 11,"name": "sunm xing"},
		{"age": 44,"id": 12,"name": "test abc"}
		] | filter:{'name':'iphone'} }}        
		
	2、limitTo 截取
		
		{{"1234567890" | limitTo :6}} // 从前面开始截取6位
		{{"1234567890" | limitTo:-4}} // 从后面开始截取4位
		
	3、orderBy 排序
		
		 // 根id降序排
		{{ [{"age": 20,"id": 10,"name": "iphone"},
		{"age": 12,"id": 11,"name": "sunm xing"},
		{"age": 44,"id": 12,"name": "test abc"}
		] | orderBy:'id':true }}
		
		// 根据id升序排
		{{ [{"age": 20,"id": 10,"name": "iphone"},
		{"age": 12,"id": 11,"name": "sunm xing"},
		{"age": 44,"id": 12,"name": "test abc"}
		] | orderBy:'id' }}

	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p><input type="text" ng-model="username"></p>
			<ul>
				<li ng-repeat="item in person | orderBy:'id' | filter:username">
					{{item.name}}
				</li>
			</ul>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.person = [{id:1,name:'jack'},{id:5,name:'tom'},
			{id:3,name:'robin'},{id:2,name:'marin'},{id:4,name:'uzi'}];
		});
	</script>
#####example 13.反转
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			{{msg | reserve}}
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.msg = 'abc';
		});
		ngApp.filter('reserve', function(){
			return function(text){
				return text.split('').reverse().join('');
			};
		});
	</script>
#####example 14.Service $location
	$location
		$location.absUrl();
		$location.path();

	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p>当前URL：{{urlStr}}</p>
			<p>当前Path：{{pathStr}}</p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $location){
			$scope.urlStr = $location.absUrl();
			$scope.pathStr = $location.path();
		});
	</script>
#####example 15.Service $http
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p>Search <input type="text" ng-model="name"></p>
			<ul>
				<li ng-repeat="item in datas | filter:name">
					{{item.name + "     " + item.pName}}
				</li>
			</ul>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $http){
			$http.get('http://182.92.234.232:8090/test/data.json').then(function (response){
				$scope.datas = response.data.data;
			});
		});
	</script>
#####example 16.Service $timeout
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			{{msg}}
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $timeout){
			$scope.msg = 'Hello world';
			$timeout(function(){
				$scope.msg = 'Change Content';
			},2000);
		});
	</script>
#####example 17.Service $interval
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p>time:{{timeStr}}</p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $interval){
			$scope.timeStr = new Date().toLocaleTimeString();
			$interval(function() {
				$scope.timeStr = new Date().toLocaleTimeString();
			}, 1000);
		});
	</script>
#####example 18.自定义服务
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			{{welcome}}
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.service('customService', function(){
			this.sayHello = function() {
				return 'Hello eveybody';
			};
		});
		ngApp.controller('ngController', function($scope, customService) {
			$scope.welcome = customService.sayHello();
		});
	</script>
#####example 19.自定义filter，并结合使用Service
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<ul>
				<li ng-repeat="x in datas">{{x | myFormat}}</li>
			</ul>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.service('toHexService', function() {
			this.myFunc = function(x) { 
				return x.toString(16);
			};
		});
		ngApp.filter('myFormat',['toHexService', function(toHexService) {
			return function(x) {
				return toHexService.myFunc(x);
			};
		}]);
		ngApp.controller('ngController', function($scope){
			$scope.datas = [211,223,255];
		});
	</script>
#####example 20.$scope.$apply(function(){})
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			{{theTime}}
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.theTime = new Date().toLocaleTimeString();
			$scope.setTime = function() {
				$scope.$apply(function(){
					$scope.theTime = new Date().toLocaleTimeString();
				});
			};
			setInterval($scope.setTime, 1000);
		});
	</script>
#####example 21.$scope.$watch
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p>
				FirstName: <input type="text" ng-model="firstName"/><br>
				LastName: <input type="text" ng-model="lastName"/><br>
			</p>
			<p>
				FirstName: {{firstName}}<br>
				LastName: {{lastName}}<br>
				FullName: {{fullName}}
			</p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope) {
			$scope.firstName = "";
			$scope.lastName = "";
			$scope.$watch('firstName', function() {
				$scope.fullName = $scope.firstName + " " + $scope.lastName;
			});
			$scope.$watch('lastName', function(){
				$scope.fullName = $scope.firstName + " " + $scope.lastName;
			});
		});
	</script>
#####example 22.$scope $http
	http简写
		$http.get('/someUrl', config).then(successCallback, errorCallback);
		$http.post('/someUrl', data, config).then(successCallback, errorCallback);
		

	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<ul>
				<li ng-repeat="item in datas">{{"Name:" + item.name + " PackageName:" + item.pName}}</li>
			</ul>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $http){
			$http({
				method:'get',
				url:'http://git.boomsecret.com:8090/test/data.json'
			}).then(function successCallback(response){
				$scope.datas = response.data.data;
			}, function errorCallback(response){
				$scope.datas = response;
			});
		});
	</script>
#####example 23.ng-options
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<select ng-model="itemValue" ng-options="item.pName for item in datas"></select>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $http){
			$http({
				method:'get',
				url:'http://git.boomsecret.com:8090/test/data.json'
			}).then(function(response){
				$scope.datas = response.data.data;
			});
		});
	</script>
#####example 24.动态table
	<body>
		<table ng-app="ngApp" ng-controller="ngController">
			<tr ng-repeat="item in datas | orderBy:'pName'">
				<td>{{$index + 1}}</td>
				<td>{{item.name}}</td>
				<td>{{item.pName | uppercase}}</td>
			</tr>
		</table>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope, $http){
			$http({
				method:'get',
				url:'http://git.boomsecret.com:8090/test/data.json'
			}).then(function(response){
				$scope.datas = response.data.data;			});
		});
	</script>
	 <style>
		table, th , td {
		  border: 1px solid grey;
		  border-collapse: collapse;
		  padding: 5px;
		}
		table tr:nth-child(odd) {
		  background-color: #f1f1f1;
		}
		table tr:nth-child(even) {
		  background-color: #ffffff;
		}
	</style> 
#####example 25.ng-disabled 
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<div>
				<button ng-disabled="myController">Button</button>
			</div>
			<div>
				<input type="checkbox" ng-model="myController"/>value
			</div>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope) {
		});
	</script>
#####example 26.ng-hide ng-show
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p>
				<input type="checkbox" ng-model="showOrHide">
			<button ng-show="showOrHide">show Or not</button>
			</p>
			<p>
				<input type="checkbox" ng-model="showOrHide1">
			<button ng-hide="showOrHide1">show Or not</button>
			</p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){	
		});
	</script>
#####example 27.ngApp.directive
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p template-layout></p>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.directive('templateLayout', function(){
			return {
				restrict:'A',
				template:'This is template'
			};
		});
		ngApp.controller('ngController', function($scope, $http){
			
		});
	</script>
#####example 28.angular.copy
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<form novalidate>
				firstName <input type="text" ng-model="user.firstName"><br>
				lastName <input type="text" ng-model="user.lastName"><br>
				<button ng-click="reset()">reset</button><br>
				User:{{user}}<br>
				Master:{{master}}
			</form>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.master = {firstName:'HH', lastName:'KK'};
			$scope.reset = function() {
				$scope.user = angular.copy($scope.master);
			}
			$scope.reset();
		});
	</script>
#####example 29.表单验证
	$dirty 	表单有填写记录
	$valid 	字段内容合法的
	$invalid 	字段内容是非法的
	$pristine 	表单没有填写记录
	
	<body>
		<form name="dataForm" ng-app="ngApp" ng-controller="ngController" novalidate>
			<p>
				username <input type="text" name="username" ng-model="username" required>
				<span style="color:red" ng-show="dataForm.username.$dirty && dataForm.username.$invalid">
					<span ng-show="dataForm.username.$error.required">用户名是必须的</span>
				</span>
			</p>
			<p>
				email <input type="email" name="email" ng-model="email" required>
				<span style="color:red" ng-show="dataForm.email.$dirty && dataForm.email.$invalid">
					<span ng-show="dataForm.email.$error.required">邮箱是必须的</span>
					<span ng-show="dataForm.email.$error.email">请输入正确邮箱</span>
				</span>
			</p>
		</form>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.username = 'jack';
			$scope.email = 'jack@163.com';
		});
	</script>
#####example 30.AngularJs API
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			json To uppercase:  {{str1}}<br>
			JSON To lowercase:  {{str2}}<br>
			Json isString:  {{str3}}<br>
			324 isNumber: {{str4}}
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.str1 = angular.uppercase("json");
			$scope.str2 = angular.lowercase("JSON");
			$scope.str3 = angular.isString("ss");
			$scope.str4 = angular.isNumber("ss");
		});
	</script>
#####example 31.Angular bootstrap
	<body ng-app="ngApp" ng-controller="ngController">
		<div class="container">
			<h3>Users</h3>
			<table class="table table-striped">
				<thead>
					<tr>
						<th>Edit</th>
						<th>FirstName</th>
						<th>LastName</th>
					</tr>
				</thead>
				<tbody>
					<tr ng-repeat="user in users">
						<td>
							<button class="btn" ng-click="editUser(user.id)">
								<span class="glyphicon glyphicon-pencil"></span>&nbsp;&nbsp;Edit
							</button>
						</td>
						<td>{{user.firstName}}</td>
						<td>{{user.lastName}}</td>
					</tr>
				</tbody>
			</table>
			<hr>
			<button class="btn btn-success" ng-click="editUser('new')">
				<span class="glyphicon glyphicon-user"></span>&nbsp;&nbsp;Create New User
			</button>
			<h3 ng-show="edit">Create New User</h3>
			<h3 ng-hide="edit">Edit User</h3>
			<hr>
			<div>
				<button class="btn btn-success" ng-disabled="error || incomplete">
				  <span class="glyphicon glyphicon-save"></span> Save Changes
				</button>
			</div>
		</div>
	</body>
	<link rel="stylesheet" type="text/css" href="css/bootstrap.min.css"/>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.edit = true;
			$scope.users = [
				{id:1, firstName:'wgg', lastName:'zkk'},
				{id:2, firstName:'qgg', lastName:'skk'},
				{id:3, firstName:'sgg', lastName:'ukk'},
				{id:4, firstName:'dgg', lastName:'ekk'},
				{id:5, firstName:'zgg', lastName:'tkk'}
			];
			$scope.editUser = function(text) {
				if (text == 'new'){
					$scope.edit = true;
				} else {
					$scope.edit = false;
				}
			}
		});
	</script>
#####example 32.an application
	<body>
		<div ng-app="ngApp" ng-controller="ngController">
			<p>
				<textarea cols="40" rows="10" ng-model="message"></textarea>
			</p>
			<button ng-click="clear()">Clear</button>
			<button ng-click="save()">Save</button><br>
			还可以输入多少字 <span ng-init="100" ng-bind="left()"></span>
		</div>
	</body>
	<script src="js/angular.min.js"></script>
	<script type="text/javascript">
		var ngApp = angular.module('ngApp', []);
		ngApp.controller('ngController', function($scope){
			$scope.message = 'text';
			$scope.left = function() {
				return 100 - $scope.message.length;
			};
			$scope.clear = function() {
				$scope.message = '';
			};
			$scope.save = function(){
				alert('note saved.');
				$scope.clear();
			};
		});
	</script>
#####exmaple 33.route, animation, di