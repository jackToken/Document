###AngularJs笔记
	<script src="js/angular.min.js"></script>
	ng-app: define application
	ng-controller: define controller
	ng-init: module init
	ng-model: model
	ng-bind: bind as innerHTML
	{{bind_name}}: output ng-model params
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

	

