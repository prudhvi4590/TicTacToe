# TicTacToe
package com.example.tictactoecheck

import android.annotation.SuppressLint
import android.os.Build
import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.annotation.RequiresApi
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.tooling.preview.Preview
import com.example.tictactoecheck.ui.theme.TicTacToeCheckTheme

class MainActivity : ComponentActivity() {
    @RequiresApi(Build.VERSION_CODES.O)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            TicTacToeCheckTheme {
                // A surface container using the 'background' color from the theme
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                    GameScreen(
                        // turn hint should be removed by win notification
                        //state is getting zero on orientation configuration change
                        // is not working on landscape orientation

                    )
                }
            }
        }
    }

}

@SuppressLint("NewApi")
@Preview
@Composable
fun preview(){
    GameScreen()
}

XML-FILE

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/background_color">

    <!-- Game Board -->
    <GridView
        android:id="@+id/gridView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:numColumns="3"
        android:horizontalSpacing="16dp"
        android:verticalSpacing="16dp"
        android:padding="16dp"
        android:gravity="center"
        android:stretchMode="columnWidth"
        android:background="@drawable/board_background"
        android:layout_centerInParent="true"/>

    <!-- Buttons -->
    <Button
        android:id="@+id/buttonNewGame"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/new_game"
        android:layout_below="@id/gridView"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="32dp"/>

    <Button
        android:id="@+id/buttonUndo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/undo"
        android:layout_below="@id/gridView"
        android:layout_toLeftOf="@id/buttonNewGame"
        android:layout_marginEnd="32dp"
        android:layout_marginTop="32dp"/>

</RelativeLayout>
