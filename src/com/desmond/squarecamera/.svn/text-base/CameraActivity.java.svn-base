package com.desmond.squarecamera;



import android.annotation.TargetApi;
import android.app.Activity;
import android.app.Fragment;
import android.content.Intent;
import android.content.pm.ActivityInfo;
import android.net.Uri;
import android.os.Build;
import android.os.Bundle;
import android.view.View;
import android.view.ViewTreeObserver;
import android.view.WindowManager;


@TargetApi(Build.VERSION_CODES.HONEYCOMB)
public class CameraActivity extends Activity {

    public static final String TAG = CameraActivity.class.getSimpleName();
    public  final String ARG_REVEAL_START_LOCATION = "reveal_start_location";
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_PORTRAIT);

        if (Build.VERSION.SDK_INT < Build.VERSION_CODES.JELLY_BEAN) {
            getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN,
                    WindowManager.LayoutParams.FLAG_FULLSCREEN);
        } else {
            View decorView = getWindow().getDecorView();
            // Hide the status bar.
            int uiOptions = View.SYSTEM_UI_FLAG_FULLSCREEN;
            decorView.setSystemUiVisibility(uiOptions);
        }

        if(getActionBar() != null){
            getActionBar().hide();    
        }
        
        getWindow().setBackgroundDrawable(null);
        setContentView(R.layout.activity_camera);
       
        if (savedInstanceState == null) {
        	Fragment content = CameraFragment.newInstance();
            getFragmentManager()
                    .beginTransaction()
                    .replace(R.id.fragment_container,content )
                    .commit();
        }
    }
    
    


    public void returnPhotoUri(Uri uri) {
        Intent data = new Intent();
        data.setData(uri);

        if (getParent() == null) {
            setResult(RESULT_OK, data);
        } else {
            getParent().setResult(RESULT_OK, data);
        }

        finish();
    }

    public void onCancel(View view) {
        getFragmentManager().popBackStack();
    }

}
