# HelloCharts for Android

在最新的Gradle 8.0上面编译不过去, 自己整理之后,可以大部分运行工作,仅仅作为学习使用

其他请参考[原来的文档](https://github.com/lecho/hellocharts-android)

## Usage

Every chart view can be defined in layout xml file:

 ```xml
    <lecho.lib.hellocharts.view.LineChartView
        android:id="@+id/chart"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
 ```

 or created in code and added to layout later:

 ```java
    LineChartView chart = new LineChartView(context);
    layout.addView(chart);
 ```

 Use methods from *Chart classes to define chart behaviour, example methods:

 ```java
    Chart.setInteractive(boolean isInteractive);
    Chart.setZoomType(ZoomType zoomType);
    Chart.setContainerScrollEnabled(boolean isEnabled, ContainerScrollType type);
 ```

 Use methods from data models to define how chart looks like, example methods:

 ```java
    ChartData.setAxisXBottom(Axis axisX);
    ColumnChartData.setStacked(boolean isStacked);
    Line.setStrokeWidth(int strokeWidthDp);
 ```

 Every chart has its own method to set chart data and its own data model, example for line chart:

 ```java
    List<PointValue> values = new ArrayList<PointValue>();
    values.add(new PointValue(0, 2));
    values.add(new PointValue(1, 4));
    values.add(new PointValue(2, 3));
    values.add(new PointValue(3, 4));

    //In most cased you can call data model methods in builder-pattern-like manner.
    Line line = new Line(values).setColor(Color.BLUE).setCubic(true);
    List<Line> lines = new ArrayList<Line>();
    lines.add(line);

    LineChartData data = new LineChartData();
    data.setLines(lines);

	LineChartView chart = new LineChartView(context);
    chart.setLineChartData(data);
 ```

 After the chart data has been set you can still modify its attributes but right after that you should call
 `set*ChartData()` method again to let chart recalculate and redraw data. There is also an option to use copy constructor for deep copy of
 chart data. You can safely modify copy in other threads and pass it to `set*ChartData()` method later.


## Contributing

Yes:) If you found a bug, have an idea how to improve library or have a question, please create new issue or comment existing one. If you would like to contribute code fork the repository and send a pull request.

# License

	HelloCharts	
	Copyright 2014 Leszek Wach
	
	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at
	
	   http://www.apache.org/licenses/LICENSE-2.0
	
	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.

---
     HelloCharts library uses code from InteractiveChart sample available 
     on Android Developers page:
     
       http://developer.android.com/training/gestures/scale.html
