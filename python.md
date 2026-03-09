## 字典
### 创建
```python
# 创建一个空字典
empty_dict = {}

# 创建包含元素的字典
person = {"name": "Alice", "age": 25, "city": "Beijing"}

# 使用 dict() 函数
person2 = dict(name="Bob", age=30, city="Shanghai")

# 键可以是多种不可变类型（数字、字符串、元组等）
mixed_dict = {1: "整数键", "name": "字符串键", (1,2): "元组键"}
```
键必须是不可变类型：如整数、浮点数、字符串、元组（但元组内的元素也必须不可变）。列表、字典等可变类型不能作为键。
键必须唯一：如果同一个键出现多次，后面的值会覆盖前面的。
```
d = {"a": 1, "b": 2, "a": 3}   # 键 "a" 被重复，最终 d 为 {"a": 3, "b": 2}
```
### 访问
```
person = {"name": "Alice", "age": 25}

print(person["name"])      # 输出：Alice
# print(person["gender"])  # KeyError: 'gender'

print(person.get("gender"))           # 输出：None
print(person.get("gender", "未知"))    # 输出：未知（指定默认值）
```
方法	描述	示例
dict.keys()	返回所有键的视图	list(person.keys())
dict.values()	返回所有值的视图	list(person.values())
dict.items()	返回所有键值对的视图	list(person.items())
dict.get(key[, default])	获取键对应的值，不存在则返回默认值	person.get("name", "未知")
dict.pop(key[, default])	删除指定键并返回其值，不存在则返回默认值或抛出异常	person.pop("age")
dict.popitem()	删除并返回一个任意的键值对（Python 3.7+ 删除最后一个插入的键值对）	k, v = person.popitem()
dict.update(other_dict)	用另一个字典更新当前字典（相同键覆盖，新键添加）	person.update({"age": 26, "gender": "F"})
dict.setdefault(key[, default])	如果键存在，返回其值；否则插入键并设为默认值	person.setdefault("country", "China")
dict.copy()	返回字典的浅拷贝	new_dict = person.copy()
dict.clear()	清空字典	person.clear()
