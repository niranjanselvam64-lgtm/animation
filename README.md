# Ex.No: 11 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:



## PROGRAM:
```
/*
Program to display animation operation”.
Developed by:Niranjan.S
Registeration Number :212225040281
*/
```
## activity_main.xml
```
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center_horizontal"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageview"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_marginTop="40dp"
        android:contentDescription="@string/app_name"
        android:src="@drawable/img"/>

    <LinearLayout
        android:id="@+id/linear1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="30dp"
        android:orientation="horizontal"
        android:weightSum="3">

        <!--To start the blink animation of the image-->
        <Button
            android:id="@+id/blink"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/blink"
            android:textColor="@color/white" />

        <!--To start the rotate animation of the image-->
        <Button
            android:id="@+id/rotate"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/clockwise"
            android:textColor="@color/white" />

        <!--To start the fading animation of the image-->
        <Button
            android:id="@+id/fade"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/fade"
            android:textColor="@color/white" />

    </LinearLayout>

    <LinearLayout
        android:id="@+id/linear2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="30dp"
        android:orientation="horizontal"
        android:weightSum="3">

        <!--To start the move animation of the image-->
        <Button
            android:id="@+id/move"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/move"
            android:textColor="@color/white" />

        <!--To start the slide animation of the image-->
        <Button
            android:id="@+id/slide"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/slide"
            android:textColor="@color/white" />

        <!--To start the zoom animation of the image-->
        <Button
            android:id="@+id/zoom"
            style="@style/TextAppearance.MaterialComponents.Button"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_margin="10dp"
            android:layout_weight="1"
            android:padding="3dp"
            android:text="@string/zoom"
            android:textColor="@color/white" />

    </LinearLayout>

    <!--To stop the animation of the image-->
    <Button
        android:id="@+id/stop"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginTop="30dp"
        android:layout_marginRight="30dp"
        android:text="@string/stop_animation" />

</LinearLayout>
```
## MainActivity.java
```
package com.example.animation;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare variables for ImageView and Buttons
    private ImageView imageView;
    private Button blink, rotate, fade, move, slide, zoom, stop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize ImageView and Buttons using their IDs
        imageView = findViewById(R.id.imageview);
        blink = findViewById(R.id.blink);
        rotate = findViewById(R.id.rotate);
        fade = findViewById(R.id.fade);
        move = findViewById(R.id.move);
        slide = findViewById(R.id.slide);
        zoom = findViewById(R.id.zoom);
        stop = findViewById(R.id.stop);

        // Set up click listeners for each button to start corresponding animations
        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(move, R.anim.move);
        createAnimation(slide, R.anim.slide);
        createAnimation(zoom, R.anim.zoom);

        // Set up click listener for stop button to clear any ongoing animation
        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    // Function to set up an animation for a given view and animation resource ID
    private void createAnimation(View view, int animResId) {
        view.setOnClickListener(v -> {
            // Load the animation from the specified resource ID
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            // Start the animation on the ImageView
            imageView.startAnimation(animation);
        });
    }
}
```
## string.xml
```
<?xml version="1.0" encoding="utf-8"?>
<resources>

    <string name="app_name">Animation App</string>

    <string name="blink">Blink</string>
    <string name="clockwise">Clockwise</string>
    <string name="fade">Fade</string>
    <string name="move">Move</string>
    <string name="slide">Slide</string>
    <string name="zoom">Zoom</string>
    <string name="stop_animation">Stop Animation</string>

</resources>
```
## blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```
## fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/accelerate_interpolator">

    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />

    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />

</set>
```
## move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">

    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```
## rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```

## OUTPUT
<img width="1920" height="1080" alt="Screenshot (76)" src="https://github.com/user-attachments/assets/aeb4650d-b7f6-428e-a0b7-e29a818df3d4" />
<img width="1920" height="1080" alt="Screenshot (79)" src="https://github.com/user-attachments/assets/379f227c-8f92-4375-a32a-563709b42ff5" />
<img width="1920" height="1080" alt="Screenshot (78)" src="https://github.com/user-attachments/assets/e4f71ecf-9dbb-4a03-8d76-b0b2761248cf" />





## RESULT
coding done sucessfully.
