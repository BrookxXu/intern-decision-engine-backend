1. The maximum loan period can be 48 months not 60.
2. The class Decision can be defined as a record(I will leave it be).
3. When encountering an error, we always set amount and period to null, we can put this logic into a method(See setError in [DecisionResponse.java](src%2Fmain%2Fjava%2Fee%2Ftaltech%2Finbankbackend%2Fendpoint%2FDecisionResponse.java)).
4. Despite the remark 3, I don't see the necessity of the class DecisionResponse. I might use Decision for response body(Still leave it be).
5. **Also, I don't think we need to autowire DecisionResponse, it's not a singleton and does not hold configurations. This could lead to unexpected data corruption in multi-threaded environments.(Fixed)**
6. In class DecisionEngine, the method getCreditModifier returns 0(And it's used at line 50) when it's debt. For easier management and flexibility, I suggest to change it with a configured constant.
7. Three exception classes are defined for input checking, I think we only need one class.
8. In class DecisionEngine, it's not appropriate to make creditModifier a field, it should belong to the method.
9. **The scoring algorithm is missing(Fixed).**
10. In the test file, not all the numbers should be hard coded.