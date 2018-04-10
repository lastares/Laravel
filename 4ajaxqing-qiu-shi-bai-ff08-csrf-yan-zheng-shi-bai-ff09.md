```
<meta name="_token" content="{{ csrf_token() }}"/>
beforeSend: function(request) {
    return request.setRequestHeader('X-CSRF-Token', $("meta[name='_token']").attr('content'));
}

```



