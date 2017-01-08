---
layout: post
title:  "Elm User Input - Buttons"
categories: Elm
---

```
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)


main =
  Html.beginnerProgram { model = model, view = view, update = update }


-- MODEL //상태를 나타냄

type alias Model = Int //count 값을 저장

model : Model
model =
  0


-- UPDATE //Model을 업데이트 하는 방법 (UI를 통해서)

type Msg = Increment | Decrement

update : Msg -> Model -> Model
update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1


-- VIEW

view : Model -> Html Msg
view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

# Reset Button 추가

Update 부분과 View 부분에서만 수정이 있었다.

```
-- UPDATE

type Msg = Increment | Decrement | Reset //Msg 추가

update : Msg -> Model -> Model
update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1
      
    Reset ->          //case추가
      model - model   //model = 0으로 하면 오류가 난다. 음...


-- VIEW

view : Model -> Html Msg
view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , div [] [button [ onClick Increment ] [ text "+" ]] //html에서 div는..?
    , button [ onClick Reset] [text "Reset"] //reset button 추가
    ]
```

html에 대해서 공부해야겠다.