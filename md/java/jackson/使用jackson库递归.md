```java
private static void recursionJsonNode(JsonNode node, SortedMap<String, String> jsonBodyMap) {  
    if (node.isValueNode() && log.isWarnEnabled()) {  
        log.warn("signParam.recursionJsonNode, node is ValueNode, node: {}", node);  
    }    if (node.isObject()) {  
        Iterator<Map.Entry<String, JsonNode>> it = node.fields();  
        while (it.hasNext()) {  
            Map.Entry<String, JsonNode> entry = it.next();  
            JsonNode value = entry.getValue();  
            if (value.isObject()) {  
                recursionJsonNode(value, jsonBodyMap);  
            }  
            if (value.isArray()) {  
                recursionJsonNode(value, jsonBodyMap);  
            }  
            if (value.isValueNode()) {  
                jsonBodyMap.put(entry.getKey(), value.asText());  
            }  
        }  
    }  
    if (node.isArray()) {  
        for (JsonNode jsonNode : node) {  
            recursionJsonNode(jsonNode, jsonBodyMap);  
        }  
    }  
}
```