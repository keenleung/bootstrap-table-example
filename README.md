<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="zh-cn">
<head>
	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8" />
	<title>网页标题</title>
	<meta name="keywords" content="关键字列表" />
	<meta name="description" content="网页描述" />
	<link rel="stylesheet" href="lib/bootstrap.min.css">
    <!-- table css-->
    <link rel="stylesheet" href="lib/bootstrap-table.css">

    <script src="lib/jquery-1.11.1.min.js"></script>
    <script src="lib/bootstrap.min.js"></script>
    <!--table js-->
    <script src="lib/bootstrap-table.js"></script>
    <script>
        $(function(){
            var data = [
                {uid : "7791", name : "keenleung1", age : "26", height : "165", description : "描述"},
                {uid : "7792", name : "keenleung2", age : "26", height : "165", description : "描述"},
                {uid : "7793", name : "keenleung3", age : "26", height : "165", description : "描述"},
                {uid : "7794", name : "keenleung4", age : "26", height : "165", description : "描述"},
                {uid : "7795", name : "keenleung5", age : "26", height : "165", description : "描述"},
            ];

            $('#table').bootstrapTable('load', data);

            var $result = $('#eventsResult');

            // 选择一行
            $('#table').on('click-row.bs.table', function (e, row, $element) {
				alert(JSON.stringify(row.uid));
            });
        });

        function actionFormatter(value, row, index) {
            return [
                "<button class='btn btn-primary like'>选取</button>",
                "<button class='btn btn-default unlike'>取消</button>",
            ].join('');
        }

        window.actionEvents = {
            'click .like': function (e, value, row, index) {
                alert(JSON.stringify(row));
                return false;
            },
            'click .unlike': function (e, value, row, index) {
                alert("unlike click");
                return false;
            },
        };
    </script>
	<style type="text/css"></style>
	<script type="text/javascript"></script>
</head>
<body>

    <div class="alert alert-success" id="eventsResult">
        Here is the result of event.
    </div>
    <table id="table"
        data-toggle="table">
        <thead>
        <tr>
            <th data-field="name">姓名</th>
            <th data-field="age">年龄</th>
            <th data-field="height">身高</th>
            <th data-field="description">描述</th>
            <th class="text-left" data-field="action" data-formatter="actionFormatter" data-events="actionEvents">操作</th>
        </tr>
        </thead>
    </table>


<script src="lib/bootstrap-table-zh-CN.js"></script>
</body>
</html>
