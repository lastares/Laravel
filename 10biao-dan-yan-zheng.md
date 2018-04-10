```php
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



