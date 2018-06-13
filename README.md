# ABanner
how to use :

  1.in your xml:
  
      <com.youth.banner.Banner
        android:id="@+id/home_banner"
        android:layout_width="match_parent"
        android:layout_height="220dp"
        app:bottom_margin="20dp"
        app:indicator_drawable_selected="@drawable/indicator_sel"
        app:indicator_drawable_unselected="@drawable/indicator_norm" />
        
        
  2.find this view
     
     Banner mTopBanner = (Banner)findViewById(R.id.home_banner);      
  
  3.You should create a class in order to load the image, 
  you can customize your own loading method in this class. eg:
    
    public class GlideImageLoad extends ImageLoader {
  
        @Override
        public void displayImage(Context mContext, Object path, ImageView imageView) {
            RequestOptions options = new RequestOptions()
                    .placeholder(R.color.white)
                    .error(R.color.white);
            Glide.with(mContext).load((String) path).apply(options).into(imageView);
        }
      }
  
  4.Set up the data source
      
      mTopBanner.setImages(images).setImageLoader(new GlideImageLoad()).start();
