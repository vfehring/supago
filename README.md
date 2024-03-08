# Supago

Unofficial [Supabase](https://supabase.com) client in Go.

## Installation
```
go get github.com/vfehring/supago
```

## Usage
```golang
import supabase "github.com/vfehring/supago"

func main() {
  supabaseUrl := "<SUPABASE_URL>"
  supabaseKey := "<SUPABASE_KEY>"
  supabaseClient := supabase.CreateClient(supabaseUrl, supabaseKey)

  // Auth
  user, err := supabaseClient.Auth.SignIn(supabase.UserCredentials{
    email: "example@example.com",
    password: "password"
  })
  if err != nil {
    panic(err)
  }

  // DB
  var results map[string]interface{}
  err = supabaseClient.DB.From("something").Select("*").Single().Execute(&results)
  if err != nil {
    panic(err)
  }

  fmt.Println(results)
}
```

## Roadmap
- [x] Auth Support
- [x] DB Support
- [ ] Realtime
- [ ] Storage
- [ ] Testing
