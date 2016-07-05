---
layout: post
title:  Unity Script Sample
date:   2016-07-05 오전 7:24:03 
categories: Unity
tags: Unity
---

시간에 따라 특정값 속도로 오브젝트를 회전시킬 때
{% highlight ruby %}
public class sample : MonoBehaviour
{

	public 


    void Update()
    {
        transform.Rotate(new Vector3(1.0f, 1.0f, 1.0f));
    }

}

{% endhighlight %}

