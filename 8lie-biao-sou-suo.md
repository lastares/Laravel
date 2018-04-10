##### 方法1

```
protected static function search($data = [])
    {
        $query = new self();
        $query = isset($data['score']) && $data['score']!='' ? $query->where('workorder.score',$data['score']) : $query;
        $query = isset($data['loan']) && $data['loan']!='' ? $query->where('workorder.loan',$data['loan']) : $query;
        return $query;
    }

```



