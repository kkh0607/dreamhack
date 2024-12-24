# csrf-2

전형적인 csrf 문제이다, csrf-1 문제를 풀었다면 아마 바로 풀거라고 생각함

``` python
@app.route("/change_password")
def change_password():
    pw = request.args.get("pw", "")
    session_id = request.cookies.get('sessionid', None)
    try:
        username = session_storage[session_id]
    except KeyError:
        return render_template('index.html', text='please login')

    users[username] = pw
    return 'Done'
```
![image](https://github.com/user-attachments/assets/6dc99c7a-2282-4157-bb4e-b0d6a80ce07a)

동일한 인터페이스이지만 app.py 코드를 잘 살펴보면 on 이 필터링 되어있어서 onerror는 못쓴다, 뭐 그냥 change_password 페이지만 불러오면 되니까 <img src={payload} ></img> 방식으로 admin 패스워드를 변경한 뒤 admin으로 다시 로그인하면 flag를 가질 수 있다.
