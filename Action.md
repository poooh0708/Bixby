# Action

## description
```

그냥 설명임

```


## type



```
1. Search
: 찾는거
2. Calculation
: An isolated computation on the inputs ...
계산하는 거인듯 
3. Constructor
: 제공된 인풋만으로 독립된 아웃풋 형성
4. Fetch
: 인풋과 directly 연결된 간단한 정보 검색
5. BeginTransaction
: transaction 에 concept을 outputs한다 
6. UpdateTransaction
: transaction 에 concept를 update (이 때 아웃풋은 trasaction의 concept이며, action 의 input임)
7. CancelTranscation
: Transcation에 concept 없앰 (이때 없어지는 concept는 action의 input임)
8. Commit
: transaction 의 concept를 최종 결정함.
9. RefreshActivity
: 


```

## collect

*input순서 계산 순서*

1. computed-input (<type>)

```
뭔가 other input으로부터 온거 ... 인듯?
computed-input (deliveryAddress) {
      type (DeliveryAddress)
      min (Required) max (One)
      compute {
        if (exists(deliveryAddress)) {
          value: $expr(deliveryAddress)
        }
      }
      
```

2. input

```
input (%name%) {
      type (%type%)     ==> input의 type
      min (%Fmin-cardinality%)
      max (%max-cardinality%)
      prompt-behavior (%prompt-behavior%)
      instantiation-behavior (%instantiation-behavior%)
      plan-behavior (%plan-behavior%)
      hidden      ==> Hide this input from function implementations
      related-values (%related-value%)
      [iterable]
      validate {
        %validation%
      }
      default-init {    ==> input이나 variable type의 default value.
        intent{   ==> A set of signals that the Bixby planner interprets to create a plan.
          goal: %goal%
          ...
        }
      }
    }
   
```

3. inputgroup

```
input-group (countryCode) {

       // require at least either a two letter country code (e.g. 'US') or a three letter country code (e.g. 'USA')
       requires (OneOf)
       collect {
         input (two_letter_code) {
           type (ISOCountryCode2)
           min (Optional)
         }
         input (three_letter_code) {
           type (ISOCountryCode3)
           min (Optional)
         }
       }
     }
```

# js
## js API 연동

*개념정리

1. [capsule configuration](https://bixbydevelopers.com/dev/docs/reference/ref-topics/capsule-config)
```
capsule code editing 없이 바꾸고 싶은 configuration data를 저장하는 방법
1) capsule.properties file
2) Bixby Developer center

==> API key 같은 것들 sensitive 해서 Secrets section 에 저장해라!
Secrets are sensitive information that should not be stored in code and might need to be updated frequently, such as API keys or other authentication details. By entering these in the Secrets section of the Bixby Developer Center, they will be securely encrypted end-to-end, and will even appear obfuscated in the Developer Center's UI. Secrets can be updated at any time.

Static, non-sensitive information that isn't likely to change often should be defined in the capsule.properties file. This could include endpoint URIs, permission scopes, and feature gates.

By setting dynamic properties in the Config section of the Bixby Developer Center, you can change property values without editing capsule code. If you define capsule properties in the Developer Center with the same names as properties in the capsule.properties file, the dynamic values will override the static ones in the file. Delete these dynamic properties to return to the values defined in the file.


```

2.
     



