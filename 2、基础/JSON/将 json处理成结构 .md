```
func main() {
  //Original struct
  orig := new(Employee)

  t := reflect.TypeOf(orig)
  v := reflect.New(t.Elem())

  // reflected pointer
  newP := v.Interface()

  // Unmarshal to reflected struct pointer
  json.Unmarshal([]byte("{\"firstname\": \"bender\"}"), newP)

  fmt.Printf("%+v\n", newP)
}
```

