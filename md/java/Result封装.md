
import lombok.EqualsAndHashCode;
import lombok.NoArgsConstructor;

import java.util.HashMap;
import java.util.Objects;

/**
 * @author BingChunMoLi
 */

@Data
@NoArgsConstructor
@EqualsAndHashCode(callSuper = true)
public class Result extends HashMap<String, Object> {
    public static final String CODE_NAME = "code";
    public static final String MSG_NAME = "message";
    public static final String DATA_NAME = "data";

    private Integer code;
    private Object data;

    public enum Code {
        //成功
        SUCCESS(0),
        //警告
        WARN(201),
        //错误
        ERROR(500);
        private final int value;

        public int code() {
            return this.value;
        }

        Code(int value) {
            this.value = value;
        }
    }

    public Result(Code code,String message){
        super.put(CODE_NAME,code.value);
        super.put(MSG_NAME, message);
    }

    public Result(Code code,String message,Object data){
        super.put(CODE_NAME,code.value);
        super.put(MSG_NAME, message);
        if (Objects.nonNull(data)){
            super.put(DATA_NAME, data);
        }
    }

    @Override
    public Result put(String key,Object value){
        super.put(key, value);
        return this;
    }

    public static Result success(){
        return success("一切OK");
    }

    public static Result success(String message){
        return new Result(Code.SUCCESS, message);
    }

    public static Result success(Object data){
        return success("成功", data);
    }
    public static Result success(String message,Object data){
        return new Result(Code.SUCCESS,message, data);
    }


    public static Result warn(){
        return warn("警告");
    }

    public static Result warn(String message){
        return new Result(Code.WARN,message);
    }

    public static Result warm(Object data){
        return success("警告", data);
    }

    public static Result warn(String message,Object data){
        return new Result(Code.WARN, message, data);
    }

    public static Result error(){
        return warn("失败");
    }

    public static Result error(String message){
        return new Result(Code.WARN,message);
    }

    public static Result error(Object data){
        return success("失败", data);
    }

    public static Result error(String message,Object data){
        return new Result(Code.ERROR, message, data);
    }

}
