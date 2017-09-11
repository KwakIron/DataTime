# DataTime
```
package com.guozhe.android.datatime;

import android.os.Bundle;
import android.support.annotation.NonNull;
import android.support.v7.app.AppCompatActivity;
import android.widget.CalendarView;
import android.widget.DatePicker;
import android.widget.TimePicker;
import android.widget.Toast;

import java.util.Calendar;

public class MainActivity extends AppCompatActivity implements DatePicker.OnDateChangedListener{
    int dayOfMonth;
    int monthOfYear;
    int year;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        DatePicker dp_test = (DatePicker)findViewById(R.id.dp_test);
        Calendar calendar = Calendar.getInstance();
        year = calendar.get(Calendar.YEAR);
        monthOfYear = calendar.get(Calendar.MONTH);
        dayOfMonth = calendar.get(Calendar.DAY_OF_MONTH);
        dp_test.init(year,monthOfYear,dayOfMonth,this);

        TimePicker tp_test = (TimePicker) findViewById(R.id.tp_test);
        tp_test.setOnTimeChangedListener(new TimePicker.OnTimeChangedListener() {
            @Override
            public void onTimeChanged(TimePicker timePicker, int i, int i1) {
                Toast.makeText(MainActivity.this,"您选择的时间是："+i+"时"+i1+"分!",Toast.LENGTH_SHORT).show();
            }
        });

        CalendarView cv_test =(CalendarView) findViewById(R.id.cv_test);
        cv_test.setOnDateChangeListener(new CalendarView.OnDateChangeListener() {
            @Override
            public void onSelectedDayChange(@NonNull CalendarView calendarView, int i, int i1, int i2) {
                Toast.makeText(MainActivity.this,"您选择的时间是："+ i + "年" + i1 + "月" + (i2+1) + "日",Toast.LENGTH_SHORT).show();
            }
        });

    }

    @Override
    public void onDateChanged(DatePicker datePicker, int i, int i1, int i2) {
        Toast.makeText(MainActivity.this,"您选择的日期是："+i+"年"+(i1+1)+"月"+i2+"日!",Toast.LENGTH_SHORT).show();
    }
}
