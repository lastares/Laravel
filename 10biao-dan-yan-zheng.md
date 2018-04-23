##### 方法1

```
<?php

namespace App\Http\Controllers\Trade;

use App\Http\Models\Trade\Order;
use Illuminate\Http\Request;
use Validator;

trait FormFields
{
    public function validCreateOrder(Request $request)
    {

        // ====== 订单信息 ======
        $rules['type_order'] = 'required';
        $rules['purchase_name'] = 'required|string|between:4,20';
        $rules['purchase_mobile'] = 'required|mobile';
        $rules['purchase_id_card'] = 'required|id_card';
        $rules['supplier_name'] = 'required';
        $rules['supplier_type'] = 'required|numeric';
        $rules['car_info_color_out.' . $k] = 'required';
            $rules['car_info_color_in.' . $k] = 'required';
            $rules['car_info_fee.' . $k] = 'required|numeric';
        }
        $rules['logistics_type'] = 'required|numeric';
        if ($request->input('logistics_type')) {
            $rules['send_car_time'] = 'required';
            if ($request->input('need_logistics', 0)) {
                $rules['logistics_invoice_title'] = 'required';
                $rules['allow_last_time'] = 'required';

            }
    }
        $error = [
            'required' => '字段 :attribute 必填',
            'mobile' => '字段 :attribute 不是手机号',
            'id_card' => '字段 :attribute 不是正确的身份证号',
        ];
        $validation = Validator::make($request->all(), $rules, $error);
        return $validation->fails() ? $validation->errors()->first() : true;
    }

#################################################################
#使用方法：                                                     #
#        $valid = $this->validCreateOrder($request);            #
#       if ($valid !== true) {                                  #
#           return $this->error($valid);                        #
#       }                                                       #
#                                                               #
#################################################################
```

##### 方法2

```
protected  static function validBaseInfo($params)
    {
        $rules = [
            'salesman_id' => 'required|numeric',
            //'salesman_name' => 'required',
            'username' => 'required',
            'mobile'    => 'required',
            'ID_card' => 'required',

            //'payment_nature' => 'required|numeric|in:1,2,3',//款项性质
            //'pay_type' => 'required|numeric|in:1,2,3,4,5,6',//付款方式
            //'summary' => 'max:255',//zhaiyao
        ];
        $errors = [
            'required' => ':attribute不能为空',
            //'payment_nature.in' => '款项性质不在列表内，请先确认～',
            //'pay_type.in' => '付款方式不在列表内，请先确认～',
            //'product_plan.max' => '方案名称不能超过30字',
        ];
        $attr = [
            'salesman_id' => '业务员信息',
            //'salesman_name' => '业务员姓名',
            'username' => '申请人姓名',
            'mobile'    => '申请人手机号',
            'ID_card' => '申请人身份证号',
            'ID_car_sdate' => '申请人身份证有效期',
            'ID_car_edate' => '申请人身份证有效期',
            'birth_date' => '申请人出生年月',
            'gender' => '申请人性别',
        ];
        $validator = Validator::make($params, $rules, $errors, $attr);
        if ($validator->fails())
        {
            return  current(current($validator->errors()->toArray()));
        }
    }
    
    
    
#################################################################
# 使用方法：
# $valid = self::validBaseInfo($params['base_info']);
# if(!empty($valid)){
#    return $this->returnData(1, $valid);
# }
#################################################################
```



