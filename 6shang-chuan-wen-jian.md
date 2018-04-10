```
public function upload() {
        $file = Request::file('file');
        $date = date("Y-m-d");
        if ( $file->isValid()){
            $dir = 'data/attachment/' . $date;
            if (!is_dir($dir)){
                mkdir($dir, 0755, true);
            }
            $fileName = time().'.'.$file->getClientOriginalExtension();
            $fileSize = $file->getSize();
            $file_mime = $file->getClientOriginalExtension();
            if(in_array($file_mime,array('jpg', 'gif', 'png')))
            {	
            	if($fileSize > 1024*5*1024){
            		return response()->json(['code' => -1, 'msg' => '文件大小必须小于5M', 'data' => []]);
            	}
            }
            if($fileSize > 1024*50*1024){
            	return response()->json(['code' => -1, 'msg' => '上传文件最大为50M', 'data' => []]);
            }
            $file->move($dir, $fileName);
            $message = ['code'=>0,'msg'=>'上传成功','data'=>$date.'/'.$fileName];
        }else {
            $message = ['code'=>2,'msg'=>'上传失败','data'=>[]];
        }
        return response()->json($message);
    }

```



