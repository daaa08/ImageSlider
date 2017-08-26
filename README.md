# viewpager 

```java
public class Adapter extends PagerAdapter {

    private int[] imgs = {R.drawable.one, R.drawable.two, R.drawable.three};  // img 담기
    private LayoutInflater inflater;
    private Context context;

    public Adapter(Context context){
        this.context = context;
    }

    @Override
    public int getCount() {   // img 개수
        return imgs.length;

    }

    @Override
    public boolean isViewFromObject(View view, Object object) {
        return view == ((LinearLayout) object);
    }

    @Override
    public Object instantiateItem(ViewGroup container, int position) {   // 각각의 아이템 인스턴스화
        inflater = (LayoutInflater)context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
        View v = inflater.inflate(R.layout.slider, container, false);
        ImageView imageView = v.findViewById(R.id.imageView);
        TextView textView = v.findViewById(R.id.textView);
        imageView.setImageResource(imgs[position]);
        textView.setText((position +1)+"번째 이미지");
        container.addView(v);  // 해당 뷰 추가
        return v;  // 뷰 반환
    }

    @Override
    public void destroyItem(ViewGroup container, int position, Object object) {  // 아이템 객체 파괴
        container.invalidate();
    }
}
```
