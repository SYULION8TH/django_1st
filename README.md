# django_1st
6회차 장고 세션 자료입니다. 

# django_2nd 
7회차 장고 세션 자료입니다. 

## 자료 1. 
```python 
# posts/models.py
class Post(models.Model):
    title = models.CharField(max_length=100)
    body = models.TextField()
    img = models.ImageField(upload_to = 'posts/image')
    created_at = models.DateTimeField(auto_now_add = True)
    updated_at = models.DateTimeField(auto_now = True)
```

## 자료 2. 
```sh
python manage.py makemigrations
python -m pip install Pillow
python manage.py makemigrations
python manage.py migrate

```

## 자료 3.
```python
# posts/admin.py
from django.contrib import admin
from .models import Post
admin.site.register(Post) 

```

## 자료 4. 
```python
#posts/models.py
  def __str__(self):
        return  self.title

```
## 자료 5. 
```python 
# posts/views.py
from django.shortcuts import render
from .models import Post # 동일 폴더의 models에서 Post를 가져옴 

def home(request):
    posts = Post.objects.all() # Post 모델의 모든 데이터를 가져오겠다
    return render(request, "posts/index.html", {"post":posts[0]})

```

## 자료 6.
```python 
#blog/settings.py
# 프로젝트 내 media 파일들이 저장되는 실제 위치
MEDIA_ROOT = os.path.join(BASE_DIR, 'media') 
# 홈페이지/media/filename과 같이 url이 설계됨
MEDIA_URL = '/media/'

```

## 자료 7. 
```python
#blog/urls.py
from django.conf import settings
from django.conf.urls.static import static

urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```
