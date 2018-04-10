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

##### 方法2

```
$where = [];
$name = trim(request()->input('name', ''));
if(!empty($name))
    $where[] = ["name", 'like', '%' . $name . '%'];

$company_name = trim(request()->input('company_name', ''));
if(!empty($company_name))
    $where[] = ["company_name", 'like', '%' . $company_name . '%'];

$mobile = trim(request()->input('mobile', ''));
$where[] = ["mobile", 'like', '%' . $mobile . '%'];

$brand_name = trim(request()->input('brand_name', ''));
$where[] = ["brand_name", 'like', '%' . $brand_name . '%'];
```

##### 方法3

```
// controller接收参数
$search = [
            'title' => $title,
            'name' => $name,
        ];
// model
public function list2(array $search=[]) {
    if (isset($search['type_title'])) {
        $query = $query->where('title', 'like', '%' . $search['title'] . '%');
    }
    if (isset($search['brand_title'])) {
        $query = $query->where('brand_title', 'like', '%' . $search['brand_title'] . '%');
    }
    $res = $query->select('*')->orderBy('id', 'desc')->paginate(15);
    return $res;
}
```



