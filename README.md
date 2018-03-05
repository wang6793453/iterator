## Gradle
[![](https://jitpack.io/v/zj565061763/iterator.svg)](https://jitpack.io/#zj565061763/iterator)

## Demo

```java
public class MainActivity extends AppCompatActivity
{
    public static final String TAG = MainActivity.class.getSimpleName();

    private List<Integer> mList = new ArrayList<>();

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        fillList();
        doPositive(true);
        doReverse(true);
    }

    private void fillList()
    {
        for (int i = 0; i < 10; i++)
        {
            mList.add(i);
        }
    }

    /**
     * 正序遍历
     */
    private void doPositive(boolean log)
    {
        FIterator<Integer> it = new FListIterator<>(mList);
        it.prepare(true); //准备正序遍历
        while (it.hasNext())
        {
            Integer item = it.next();
            if (log)
            {
                Log.i(TAG, String.valueOf(item));
            }

            if (item % 2 == 0)
            {
                it.remove(); //移除当前遍历到的对象
            }
        }
    }

    /**
     * 倒序遍历
     */
    private void doReverse(boolean log)
    {
        FIterator<Integer> it = new FListIterator<>(mList);
        it.prepare(false); //准备倒序遍历
        while (it.hasNext())
        {
            Integer item = it.next();
            if (log)
            {
                Log.e(TAG, String.valueOf(item));
            }
        }
    }
}
```