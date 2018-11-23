## Model Form
>Form을 이용해 Instance를 생성하기 위해 사용

* Model class와 자동으로 연동

```
class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        fields = [
            'content',
        ]
        widgets = {
            'content' : forms.Textarea(
                attrs={
                    'class': 'form-control',
                    'rows': 2,
                }
            )
        }

```

* `save()`가 자동으로 생성
* Model field가 Form Field로 자동 연결
 
`save()`에 `commit`속성 -> True/False(default:True)
> False일 경우 DB에 저장되지 않은 객체가 반환

```
def comment_create(request, post_pk):
    if request.method == 'POST':
        post = Post.objects.get(pk=post_pk)
        form = CommentForm(request.POST)
        if form.is_valid():
            comment = form.save(commit=False)
            comment.post = post
            comment.author = request.user
            comment.save()
            return redirect('posts:post_list')
```