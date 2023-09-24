```java
package com.bingchunmoli.api.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.oas.annotations.EnableOpenApi;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.service.Contact;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;

/**
 * @copyright(c) 2017-2020 冰纯茉莉
 * @Description: TODO Swagger配置类
 * @Author 冰彦糖
 * @Data 2020/11/11 11:50
 * @ClassName SwaggerConfig
 * @PackageName: com.bingchunmoli.api.config
 * @Version 0.0.1-SNAPSHOT
 **/

@Configuration
//@EnableSwagger2
@EnableOpenApi
public class SwaggerConfig {
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                .apis(RequestHandlerSelectors.any())
                .paths(PathSelectors.any())
                .build();
    }
    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("冰纯茉莉的 API")
                .contact(new Contact("冰纯茉莉",  "https://api.bingchunmoli.com",  "bingchunmoli@foxmail.com"))
                .version("v2.0")
                .description("公共API")
                .build();
    }
}
```