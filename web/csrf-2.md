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
