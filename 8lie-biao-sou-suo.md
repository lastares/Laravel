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



