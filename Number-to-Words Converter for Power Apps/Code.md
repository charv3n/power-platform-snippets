#YAML Code
````
- Container1:
    Control: GroupContainer
    Variant: manualLayoutContainer
    Properties:
      BorderThickness: =1
      DropShadow: =DropShadow.None
      Height: =297
      RadiusBottomLeft: =8
      RadiusBottomRight: =8
      RadiusTopLeft: =8
      RadiusTopRight: =8
      Width: =471
      X: =36
      Y: =52
    Children:
    - TextInput1:
        Control: Classic/TextInput
        Properties:
          Default: =
          HintText: ="Enter Text Here"
          BorderThickness: =0
          Clear: =true
          EnableSpellCheck: =true
          Fill: =RGBA(214, 221, 224, 1)
          Format: =TextFormat.Number
          Height: =38
          Size: =8
          Width: =405
          X: =28
          Y: =104
    - Icon1:
        Control: Classic/Icon
        Variant: Copy
        Properties:
          OnSelect: |-
            =Copy(OutputText.Text);
            Notify("Text copied");
          Color: =RGBA(0, 0, 0, 1)
          Height: =12
          Icon: =Icon.Copy
          Width: =20
          X: =433
          Y: =190
    - TextCanvas1_2:
        Control: Text
        Properties:
          Size: =11
          Text: ="Word output"
          Height: =30
          Width: =320
          X: =28
          Y: =160
    - TextCanvas1_3:
        Control: Text
        Properties:
          Size: =11
          Text: ="Numeric input"
          Height: =30
          Width: =320
          X: =28
          Y: =74
    - OutputText:
        Control: Classic/TextInput
        Properties:
          Default: "=With({\r\n    numInput: Value(TextInput1.Text),\r\n    currency: \"Dollar\"\r\n},\r\n        With({\r\n            _text: Text(numInput,\"000 000 000 000 000.00\"),\r\n            _maxPlace: RoundUp(Len(Text(numInput,\"0\"))/3,0)+1,\r\n            _places: [\" Trillion \",\" Billion \",\" Million \",\" Thousand \",\r\n                           If(Text(RoundDown(numInput,0),\"0\")=\"1\" \r\n                                ,\" \"& currency &\" and \"\r\n                                ,\" \"& currency &\"s and \"\r\n                           )\r\n                        ,\" Cents\"],\r\n            _zero: \"Zero\",\r\n            _hundred: \"Hundred\",\r\n            _ones: [\"One\", \"Two\", \"Three\", \"Four\", \"Five\", \"Six\", \"Seven\", \"Eight\", \"Nine\"],\r\n            _teens: [\"Eleven\", \"Twelve\", \"Thirteen\", \"Fourteen\", \"Fifteen\", \"Sixteen\", \"Seventeen\", \"Eighteen\", \"Nineteen\"],\r\n            _tens: [\"Ten\",\"Twenty\", \"Thirty\", \"Forty\", \"Fifty\", \"Sixty\", \"Seventy\", \"Eighty\", \"Ninety\"]\r\n        },\r\n            With({\r\n                _vals: With({\r\n                            XAll: LastN(Split(_text,\" \"),_maxPlace-1)\r\n                        },\r\n                            Filter(Ungroup(\r\n                                    Table(\r\n                                        {NumX: If(_maxPlace>2,FirstN(XAll,_maxPlace-2),Blank())},\r\n                                        {NumX: Split(Last(XAll).Value,\".\")}\r\n                                    ),\r\n                                    NumX\r\n                                ) As U\r\n                            ,!IsBlank(U.Value))\r\n                        ),\r\n                _selPlace: LastN(_places,_maxPlace)\r\n            },\r\n            With({\r\n                _TempTable: ForAll(Sequence(_maxPlace,1,1) As X ,\r\n                    {\r\n                            _Amount: Value(Last(FirstN(_vals,X.Value)).Value),\r\n                            _Place: Last(FirstN(_selPlace,X.Value)).Value\r\n                    }\r\n                )\r\n            },\r\n                With({\r\n                    _ABC:\r\n                        ForAll(_TempTable As Y,\r\n                            With(\r\n                                {\r\n                                    _mod10: Mod(Y._Amount, 10), \r\n                                    _mod100: Mod(Y._Amount, 100),\r\n                                    _HUNDREDS: Value(Left(Y._Amount, 1)),\r\n                                    _TENS: Value(Left(Mod(Y._Amount, 100),1))\r\n\r\n                                },\r\n                                {\r\n                                    Ress:   \r\n                                            If(\r\n                                            //numInput = 1, First(_ones).Value &currency,\r\n                                            numInput = 0, _zero,\r\n\r\n                                            //Zeros\r\n                                            And(\r\n                                                Or(Y._Amount = 0,IsBlank(Y._Amount))\r\n                                                ,Y._Place = Last(_places).Value\r\n                                                ), _zero,\r\n                                            \r\n                                            //Default\r\n                                            If(Y._Amount >= 100,\r\n                                                        Concatenate(\r\n                                                            Last(FirstN(_ones,_HUNDREDS)).Value,\r\n                                                            \" \" & _hundred,\r\n                                                            If(_mod100>0, \" and \", \"\")\r\n                                                        )\r\n                                                    )\r\n                                                &\r\n                                                If(_mod100 >= 20,\r\n                                                    Concatenate(\r\n                                                        Last(FirstN(_tens, _TENS)).Value,\r\n                                                        If(_mod10 > 0, \"-\" & Last(FirstN(_ones,_mod10)).Value, \"\")\r\n                                                    ),\r\n                                                    If(_mod100 > 10,\r\n                                                        Last(FirstN(_teens,_mod10)).Value,\r\n                                                        If(_mod100=0,\"\",\r\n                                                        If(_mod10=0,First(_tens).Value,Last(FirstN(_ones,_mod10)).Value))\r\n                                                    )\r\n                                                )\r\n                                            )\r\n                                    & Y._Place\r\n\r\n                                }\r\n                            )\r\n                        )\r\n                    }\r\n                    ,\r\n                    Concat(_ABC,Ress,\"\")\r\n                )\r\n            )\r\n        )\r\n    )\r\n)"
          HintText: ="Enter Text Here"
          BorderThickness: =0
          DisplayMode: =DisplayMode.View
          Fill: =RGBA(214, 221, 224, 1)
          Height: =70
          Mode: =TextMode.MultiLine
          Size: =8
          Width: =405
          X: =28
          Y: =190
    - TextCanvas1_4:
        Control: Text
        Properties:
          Size: =16
          Text: ="Number-to-Words Converter for Power Apps"
          Weight: ='TextCanvas.Weight'.Semibold
          Height: =30
          Width: =387
          X: =28
          Y: =25

````
