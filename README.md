<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
    <style type="text/css">
        body, html {
            width: 100%;
            height: 100%;
            margin: 0;
            font-family: "微软雅黑";
        }

        #allmap {
            width: 100%;
            height: 90%;
        }

        p {
            margin-left: 5px;
            font-size: 14px;
        }
    </style>
    <script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=4e9dxOHo69bEAotI6TbIKnq1	"></script>
    <script src="http://libs.baidu.com/jquery/1.9.0/jquery.js"></script>
    <title>给多个点添加信息窗口</title>
</head>
<body>
    <div id="allmap"></div>
    <span style="color:Fuchsia;">  大于2W "Fuchsia";</span>
    <span style="color:red;">  大于1.7W "red";</span>
    <span style="color:MidnightBlue;">  大于1.6W "MidnightBlue";</span>
    <span style="color:Magenta;">  大于1.5W "Magenta";</span>
    <span style="color:Indigo;">  大于1.3W "Indigo";</span>
    <span style="color:DeepPink;">  大于1.2W "DeepPink";</span>
    <span style="color:MediumSpringGreen;">  大于1.1W "MediumSpringGreen";</span>
    <span style="color:Crimson;">  大于1W "Crimson";</span>
    <span style="color:Cyan;">  小于1W "Cyan";</span>
    <br />


    <input type="text" id="dy" title="单价大于" value="9000" />
    <input type="text" id="xy" title="单价小于" value="20000" />
    <input type="button" value="加载" onclick="Jz()" />
</body>
</html>
<script type="text/javascript">



    // 百度地图API功能
    var map = new BMap.Map("allmap");
    map.centerAndZoom(new BMap.Point(115.482962, 38.869876), 17);
    map.enableScrollWheelZoom();


    function getBoundary() {
        var bdary = new BMap.Boundary();
        bdary.get("保定市竞秀区", function (rs) {       //获取行政区域
            //map.clearOverlays();        //清除地图覆盖物
            var count = rs.boundaries.length; //行政区域的点有多少个
            if (count === 0) {
                alert('未能获取当前输入行政区域');
                return;
            }
            var pointArray = [];
            for (var i = 0; i < count; i++) {
                var ply = new BMap.Polygon(rs.boundaries[i], { strokeWeight: 2, strokeColor: "#FF0000" }); //建立多边形覆盖物
                map.addOverlay(ply);  //添加覆盖物
                pointArray = pointArray.concat(ply.getPath());
            }
            map.setViewport(pointArray);    //调整视野

        });
        bdary.get("保定市莲池区", function (rs) {       //获取行政区域
            //map.clearOverlays();        //清除地图覆盖物
            var count = rs.boundaries.length; //行政区域的点有多少个
            if (count === 0) {
                alert('未能获取当前输入行政区域');
                return;
            }
            var pointArray = [];
            for (var i = 0; i < count; i++) {
                var ply = new BMap.Polygon(rs.boundaries[i], { strokeWeight: 2, strokeColor: "#00FFFF" }); //建立多边形覆盖物
                map.addOverlay(ply);  //添加覆盖物
                pointArray = pointArray.concat(ply.getPath());
            }
            map.setViewport(pointArray);    //调整视野

        });
    }


    getBoundary();


    var data_info2 = [
	[115.409463, 38.885712, "万和春天", "147", "2020", "10686", "↑1.73%", ""],
[115.470777, 38.944962, "朝阳首府", "126", "2015", "9189", "↓0.71%", ""],
[115.499938, 38.911421, "丽景蓝湾B区", "98", "2010", "16467", "↓1.94%", ""],
[115.453014, 38.910877, "华中假日丽城", "91", "2015", "11900", "↓0.43%", ""],
[115.484824, 38.932112, "香溪名门", "79", "2018", "13802", "↑2.00%", ""],
[115.564652, 38.88899, "秀兰森活里", "70", "2016", "9432", "↓10.66%", ""],
[115.501765, 38.903791, "新一代C区", "67", "2007", "13082", "↓19.94%", ""],
[115.487826, 38.941221, "阳光盛景", "66", "2014", "9161", "↓9.88%", ""],
[115.45542, 38.91672, "万和城", "66", "2013", "9636", "↓5.46%", ""],
[115.478422, 38.911305, "城市印象", "47", "2019", "16261", "↑2.57%", ""],
[115.507738, 38.904893, "秀兰锦观城", "47", "2007", "12689", "↓8.02%", ""],
[115.555008, 38.879143, "未来城", "41", "2015", "10545", "↑0.00%", ""],
[115.505377, 38.836342, "锦绣城", "39", "2012", "11375", "↑6.62%", ""],
[115.486594, 38.895448, "假日雅典城", "39", "2009", "15230", "↑1.73%", ""],
[115.458739, 38.913944, "秀兰城市美居", "38", "2012", "10667", "↑0.00%", ""],
[115.504643, 38.913711, "丽景蓝湾A区", "37", "2008", "16752", "↓2.43%", ""],
[115.499868, 38.925973, "维多利亚夏郡", "34", "2013", "9228", "↓32.69%", ""],
[115.538787, 38.864724, "东部风景", "32", "2006", "13919", "↑0.00%", ""],
[115.586541, 38.882768, "博仕园", "31", "2006", "13271", "↑0.00%", ""],
[115.576286, 38.877102, "光达e时代", "31", "2018", "11816", "↑0.00%", ""],
[115.519111, 38.904875, "秀兰尚城", "30", "2012", "12776", "↑2.22%", ""],
[115.505178, 38.913447, "丽景蓝湾", "28", "2011", "15129", "↑0.87%", ""],
[115.545753, 38.896265, "未来微墅", "28", "2018", "6404", "↑9.41%", ""],
[115.404692, 38.868289, "哈罗城", "28", "2018", "9614", "↑4.70%", ""],
[115.488972, 38.878229, "中央峰景", "28", "2009", "13470", "↓7.14%", ""],
[115.45615, 38.828117, "秀兰城市美地", "27", "2013", "11029", "↑0.00%", ""],
[115.490448, 38.912912, "公园时代", "25", "2016", "11463", "↓9.94%", ""],
[115.485813, 38.847521, "秀兰裕丰新区", "24", "2017", "11804", "↓4.07%", ""],
[115.539857, 38.881414, "新东方凤凰城", "23", "2008", "15551", "↑0.00%", ""],
[115.505519, 38.89014, "假日山水华庭", "23", "2010", "15143", "↑0.00%", ""],
[115.495713, 38.904576, "嘉兴青年新城", "23", "2008", "15529", "↓4.11%", ""],
[115.47347, 38.907396, "朝阳龙座", "22", "2008", "13703", "↑0.00%", ""],
[115.525534, 38.849974, "泰和福地水岸", "22", "2013", "6294", "↓46.19%", ""],
[115.463636, 38.901546, "水榭花城", "22", "2012", "11687", "↓11.03%", ""],
[115.563876, 38.885145, "未来石", "21", "2013", "13936", "↑0.00%", ""],
[115.523681, 38.857786, "文津花园", "21", "2017", "10916", "↑0.00%", ""],
[115.484474, 38.906381, "秀兰城市绿洲", "21", "2010", "13721", "↓10.14%", ""],
[115.521947, 38.900931, "复兴苑", "21", "2009", "15538", "↓1.03%", ""],
[115.517322, 38.919579, "溪杉樾", "20", "2018", "13777", "↓8.79%", ""],
[115.464728, 38.887365, "北基地建设家园", "19", "2006", "13955", "↓5.66%", ""],
[115.407998, 38.888628, "万和奥城", "19", "2018", "5991", "↓45.97%", ""],
[115.47213, 38.848676, "浩正渼林湾", "18", "2016", "10826", "↓3.19%", ""],
[115.451905, 38.89077, "丽景溪城", "18", "2013", "11179", "↓25.69%", ""],
[115.542068, 38.852683, "佰盛东俪湾", "18", "2008", "12365", "↓7.9%", ""],
[115.527166, 38.888512, "领秀世纪城", "18", "2012", "11525", "↓0.94%", ""],
[115.482849, 38.907714, "绿都皇城", "17", "2013", "11935", "↓7.51%", ""],
[115.471022, 38.954695, "昭华锦城", "17", "2010", "9411", "↑2.30%", ""],
[115.413235, 38.93714, "红山庄园", "16", "2013", "12779", "↓3.07%", ""],
[115.440737, 38.862785, "中诚晶典", "16", "2016", "6784", "↑0.80%", ""],
[115.516977, 38.90846, "北城枫景", "16", "2012", "8765", "↓11.79%", ""],
[115.514772, 38.905718, "秀兰钻石嘉园", "16", "2007", "13462", "↑2.80%", ""],
[115.440464, 38.86891, "香溪茗苑", "16", "2013", "12855", "↑8.49%", ""],
[115.530109, 38.895016, "清山公爵城", "16", "2016", "12901", "↓4.21%", ""],
[115.47497, 38.90293, "华中国宅华府", "15", "2015", "13210", "↓5.98%", ""],
[115.507916, 38.862124, "裕华园", "14", "2006", "12574", "↓9.79%", ""],
[115.494499, 38.911557, "丽景蓝湾C区", "14", "2015", "11946", "↓22.03%", ""],
[115.521021, 38.93134, "明珠佳苑", "14", "2014", "8584", "↓6.59%", ""],
[115.452496, 38.935031, "万和蓝山", "14", "2017", "8814", "↓26.7%", ""],
[115.48667, 38.894017, "建安三公司宿舍", "14", "2008", "11414", "↑0.00%", ""],
[115.480453, 38.853994, "世家郦园", "14", "2009", "16190", "↑0.00%", ""],
[115.53063, 38.889803, "Park湾", "13", "2013", "13815", "↑8.60%", ""],
[115.427692, 38.857162, "溪岸花语", "13", "2012", "5623", "↑0.97%", ""],
[115.468817, 38.905351, "新世纪花园", "12", "2007", "10545", "↓26.99%", ""],
[115.564018, 38.891609, "未来花郡", "12", "2016", "12853", "↑0.00%", ""],
[115.488285, 38.875643, "中央峰景B区", "12", "2017", "14703", "↓16.53%", ""],
[115.405634, 38.893433, "万和悦都", "11", "2017", "7161", "↓21.1%", ""],
[115.482243, 38.846137, "锦绣鑫城", "11", "2013", "8685", "↓1.37%", ""],
[115.518642, 38.918352, "鑫丰国际", "11", "2014", "5781", "↓1.63%", ""],
[115.489821, 38.895274, "花倾城", "10", "2008", "15139", "↓4.09%", ""],
[115.405678, 38.842329, "美林河畔", "10", "2012", "7328", "↑0.00%", ""],
[115.455084, 38.90277, "同美西鲁岗", "9", "2014", "11508", "↑4.47%", ""],
[115.50843, 38.910194, "警盾家园", "9", "2008", "15121", "↑0.00%", ""],
[115.49964, 38.914709, "盛和嘉园", "9", "2014", "16013", "↑0.00%", ""],
[115.454022, 38.898968, "博鑫青年城", "9", "2011", "12093", "↑7.17%", ""],
[115.463541, 38.866526, "晨巍佳欣", "9", "2014", "13684", "↑6.32%", ""],
[115.505167, 38.827845, "枫林花溪", "9", "2013", "8940", "↓5.83%", ""],
[115.49953, 38.886294, "大唐盛苑", "9", "2012", "10250", "↑0.00%", ""],
[115.522572, 38.870172, "上湖名郡", "9", "2014", "11754", "↓6.56%", ""],
[115.531238, 38.868997, "东方云顶", "9", "2017", "14623", "↓2.06%", ""],
[115.535556, 38.892849, "香江东湖印象", "9", "2013", "9140", "↓13.21%", ""],
[115.508431, 38.922036, "珑城花园", "8", "2010", "13734", "↑0.00%", ""],
[115.478297, 38.897066, "兴远现代城", "8", "2009", "13956", "↓6.69%", ""],
[115.457806, 38.917489, "万和城二期", "8", "2011", "13905", "↑9.08%", ""],
[115.462748, 38.883057, "向阳茗筑", "7", "2011", "14009", "↑0.00%", ""],
[115.45979, 38.897814, "世家花园", "7", "2006", "12557", "↑0.00%", ""],
[115.498708, 38.906604, "丽景华庭", "7", "2014", "9054", "↓40.49%", ""],
[115.500324, 38.906757, "天籁新城", "7", "2015", "9646", "↓7.89%", ""],
[115.510072, 38.844523, "嘉森·理想城", "7", "2013", "9178", "↑1.36%", ""],
[115.54231, 38.857058, "裕华铭珠", "7", "2015", "14184", "↓18.81%", ""],
[115.434382, 38.858438, "富景蓝湾", "7", "2014", "5216", "↑2.90%", ""],
[115.441338, 38.858227, "幸福里小区", "7", "2011", "5602", "↑0.00%", ""],
[115.462118, 38.89627, "天鹅湾", "7", "2011", "13889", "↑0.00%", ""],
[115.532782, 38.851237, "隶都景苑", "6", "2014", "8688", "↓15.7%", ""],
[115.586523, 38.884049, "博仕园二期", "6", "2015", "14084", "↑0.00%", ""],
[115.516232, 38.898085, "亢龙骏景", "6", "2015", "12348", "↑19.25%", ""],
[115.511671, 38.866601, "中华小区四区", "6", "2007", "9512", "↓4.78%", ""],
[115.514313, 38.855521, "府河美岸", "6", "2013", "11975", "↑0.00%", ""],
[115.50401, 38.911391, "华冠庄园", "6", "2007", "15941", "↑0.00%", ""],
[115.483412, 38.899862, "新一代B区", "6", "2007", "13005", "↑0.00%", ""],
[115.491702, 38.90284, "物价局宿舍", "5", "2007", "11104", "↓1.89%", ""],
[115.508153, 38.913011, "世新园小区", "5", "2010", "13316", "↑0.00%", ""],
[115.524649, 38.890706, "宜家花园", "5", "2006", "15717", "↑0.00%", ""],
[115.496456, 38.860696, "淮军公所", "5", "2006", "13637", "↑0.10%", ""],
[115.492671, 38.846876, "裕丰二期", "5", "2006", "11573", "↓8.03%", ""],
[115.474274, 38.866071, "外贸局宿舍", "5", "2010", "12682", "↓2.02%", ""],
[115.469477, 38.864497, "阳光佳苑B区", "5", "2007", "14193", "↓6.24%", ""],
[115.480337, 38.860246, "新建华小区", "4", "2007", "14167", "↓4.86%", ""],
[115.46937, 38.870385, "向阳家园", "4", "2010", "12345", "↓2.7%", ""],
[115.528664, 38.870747, "安康家园", "4", "2013", "12662", "↑0.00%", ""],
[115.523492, 38.865682, "魅力东方", "4", "2008", "16037", "↓5.87%", ""],
[115.520211, 38.882183, "名仕佳苑", "4", "2008", "14271", "↑22.04%", ""],
[115.512685, 38.85309, "金丰花园", "4", "2007", "11781", "↓13.18%", ""],
[115.458376, 38.822093, "尧和宁苑", "4", "2011", "6349", "↑0.00%", ""],
[115.481927, 38.837331, "紫横家园东区", "4", "2010", "9813", "↑11.35%", ""],
[115.515061, 38.91992, "宝石花园", "4", "2016", "12744", "↑15.03%", ""],
[115.502553, 38.887771, "翰林雅居", "4", "2013", "11349", "↑153.27%", ""],
[115.499045, 38.889466, "瑞祥大街163号院", "4", "2015", "12242", "↑0.00%", ""],
[115.52079, 38.909601, "任达佳苑", "4", "2014", "11534", "↑0.00%", ""],
[115.44174, 38.888686, "阳光水岸", "4", "2011", "10705", "↓19.24%", ""],
[115.495721, 38.896765, "九华社区", "3", "2007", "15035", "↑0.00%", ""],
[115.473685, 38.911418, "尚北岚庭", "3", "2008", "14249", "↑0.00%", ""],
[115.481941, 38.927402, "源盛嘉禾C区", "3", "2016", "14261", "↑0.00%", ""],
[115.460447, 38.883048, "海怡佳苑", "3", "2010", "15900", "↑0.00%", ""],
[115.460455, 38.880352, "乐凯佳苑", "3", "2008", "14112", "↑0.00%", ""],
[115.51118, 38.888556, "张庄小区", "3", "2010", "10042", "↑28.40%", ""],
[115.528805, 38.850247, "鑫丰·近水庭院", "3", "2014", "5823", "↓37.43%", ""],
[115.534489, 38.878152, "金顶宝座", "3", "2009", "7888", "↑6.44%", ""],
[115.480315, 38.847566, "鑫欣文雅苑", "3", "2016", "10891", "↓2.52%", ""],
[115.475349, 38.861823, "佳和小区", "3", "2006", "13395", "↑0.00%", ""],
[115.472065, 38.860464, "馨乐园", "3", "2009", "10565", "↓4.46%", ""],
[115.463696, 38.895774, "君越龙庭", "2", "2012", "13699", "↑0.00%", ""],
[115.462119, 38.900829, "今朝家园", "2", "2007", "10973", "↑21.21%", ""],
[115.461308, 38.847277, "香溪雅地", "2", "2017", "12944", "↑0.00%", ""],
[115.454138, 38.889715, "天瑞嘉苑", "2", "2010", "10724", "↑0.00%", ""],
[115.485903, 38.910585, "新光明小区", "2", "2010", "14499", "↑0.00%", ""],
[115.476082, 38.863713, "亢龙盛景", "2", "2013", "13594", "↑0.00%", ""],
[115.501306, 38.869442, "土地局宿舍(时代商厦)", "2", "2007", "12927", "↑0.00%", ""],
[115.486688, 38.859769, "星河湾", "2", "2013", "9735", "↓10.88%", ""],
[115.483796, 38.847896, "雍和嘉苑", "2", "2009", "5108", "↓40.03%", ""],
[115.492671, 38.846876, "裕丰三区二期", "2", "2014", "12585", "↑0.00%", ""],
[115.528848, 38.869424, "和谐家园", "2", "2009", "13073", "↑0.00%", ""],
[115.532744, 38.869993, "假日公馆", "2", "2006", "14034", "↑0.00%", ""],
[115.520227, 38.85332, "玫瑰公馆", "2", "2010", "14842", "↑19.53%", ""],
[115.528833, 38.864137, "悦正园", "2", "2016", "10154", "↑0.00%", ""],
[115.538279, 38.853352, "东郡绿岛", "2", "2011", "9289", "↓7.65%", ""],
[115.49579, 38.908445, "风帆家园", "2", "2016", "13159", "↓3.64%", ""],
[115.523903, 38.890061, "人民银行宿舍", "2", "2009", "9053", "↑0.00%", ""],
[115.513951, 38.851714, "幸福小区", "2", "2012", "5614", "↓13.95%", ""],
[115.509969, 38.847717, "卓雅豪庭", "2", "2010", "10069", "↑0.00%", ""],
[115.490361, 38.822471, "贺阳花园", "2", "2012", "5881", "↑0.00%", ""],
[115.492082, 38.835558, "锦绣花园", "2", "2011", "5006", "↓41.26%", ""],
[115.481698, 38.856222, "世家公馆", "2", "2012", "9846", "↑0.00%", ""],
[115.518256, 38.8911, "秀兰文景苑", "2", "2009", "14012", "↓13.53%", ""],
[115.458225, 38.859999, "四八二一区", "2", "2007", "12555", "↓4.52%", ""],
[115.468875, 38.863736, "阳光佳苑C区", "2", "2012", "12518", "↓2.2%", ""],
[115.502264, 38.861719, "总督署小区", "2", "2016", "11586", "↓16.15%", ""],
[115.492922, 38.903826, "千禧园", "2", "2012", "11482", "↑29.07%", ""],
[115.506242, 38.903824, "世纪华庭", "2", "2006", "14823", "↑0.00%", ""],
[115.484559, 38.887201, "都市华庭", "2", "2008", "12679", "↓2.97%", ""],
[115.465299, 38.896935, "都市嘉园", "2", "2006", "10800", "↑0.00%", ""],
[115.46792, 38.890646, "金阳小区", "2", "2012", "8094", "↑0.00%", ""],
[115.449751, 38.887208, "容大中院5号", "2", "2014", "6960", "↑0.00%", ""],
[115.480161, 38.895942, "城市管理局宿舍", "2", "2006", "10171", "↓2.86%", ""],
[115.478976, 38.89684, "华科新星座", "2", "2008", "15050", "↓6.23%", ""],
[115.477678, 38.893898, "九号国际城", "2", "2013", "12205", "↑0.00%", ""],
[115.498655, 38.899203, "建材小区", "2", "2007", "11569", "↓1.57%", ""],
[116.35361, 39.875427, "鹏润家园", "2", "2010", "13738", "↓5.35%", ""]
    ];



    var opts = {
        width: 250,     // 信息窗口宽度
        height: 80,     // 信息窗口高度
        title: "信息窗口", // 信息窗口标题
        enableMessage: true//设置允许信息窗发送短息
    };
    var ecec = function (data_info) {
        map.clearOverlays();
        for (var i = 0; i < data_info.length; i++) {
            var marker = new BMap.Marker(new BMap.Point(data_info[i][0], data_info[i][1]));  // 创建标注
            var content = data_info[i][2] + "-" + data_info[i][3] + "-" + data_info[i][4] + "-" + data_info[i][5] + "-" + data_info[i][6] + "-" + data_info[i][7] + "-" + data_info[i][8];
            map.addOverlay(marker);               // 将标注添加到地图中
            addClickHandler(content, marker);
            //marker.setAnimation(BMAP_ANIMATION_BOUNCE);

            var opts = {
                position: new BMap.Point(data_info[i][0], data_info[i][1]),    // 指定文本标注所在的地理位置
                offset: new BMap.Size(10, -30)    //设置文本偏移量
            }
            var label = new BMap.Label("<b>" + data_info[i][2] + "<b/> &nbsp&nbsp&nbsp&nbsp" + data_info[i][4] + "<br/>&nbsp&nbsp" + data_info[i][3] + "套———" + data_info[i][5], opts);  // 创建文本标注对象
            label.setStyle({
                color: getColor(data_info[i][5]),
                fontSize: "12px",
                height: "40px",
                lineHeight: "20px",
                fontFamily: "微软雅黑"
            });
            marker.setLabel(label);
        }
    }
    function addClickHandler(content, marker) {
        marker.addEventListener("click", function (e) {
            openInfo(content, e)
        }
		);
    }


    function openInfo(content, e) {
        var p = e.target;
        var point = new BMap.Point(p.getPosition().lng, p.getPosition().lat);
        var infoWindow = new BMap.InfoWindow(content, opts);  // 创建信息窗口对象
        map.openInfoWindow(infoWindow, point); //开启信息窗口
    }

    function getColor(num) {
        var numInt = Number(num);

        if (numInt >= 20000)
            return "Fuchsia";

        if (numInt >= 17000)
            return "red";

        if (numInt >= 16000)
            return "MidnightBlue";

        if (numInt >= 15000)
            return "Magenta";

        if (numInt >= 13000)
            return "Indigo";

        if (numInt >= 12000)
            return "DeepPink";

        if (numInt >= 11000)
            return "MediumSpringGreen";

        if (numInt >= 10000)
            return "Crimson";


        return "Cyan";
    }

    ecec(data_info2);

    function Jz() {
        debugger;
        var arr;
        if ($("#dy").val()) {
            arr = $.grep(data_info2, function (n, i) {
                return n[5] > Number($("#dy").val())
            });
        }
        if ($("#xy").val()) {
            arr = $.grep(arr, function (n, i) {
                return n[5] < Number($("#xy").val())
            });
        }
		if ($("#ts").val()) {
            arr = $.grep(arr, function (n, i) {
                return n[3] < Number($("#ts").val())
            });
        }


        ecec(arr)
    }
</script>
