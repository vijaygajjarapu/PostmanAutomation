# ds-comonea-sp-strawberry-smoke-tests

Postman smoke test suite for strawberry service (Sparkassen FI integration)

Sparkassen FI End points can be tested using .gitlab-ci.yml. Execution generates a report which can be viewed in the Artifacts Section.


Production:

To validate End points in Production, we need to use FI_Prod_SmokeTests.json.
It contains collection of GET end points.

Gitlab-ci.yml need to be updated with below command in the script Section:

- newman run FI_Prod_SmokeTests.json -e FI_environment_variables.json --reporters cli,htmlextra --reporter-htmlextra-export testReport.html


Stage:


To validate End points in Stage, we need to use FI_Stage_SmokeTests.json.
It contains collection of POST,PUT and GET end points.

Gitlab-ci.yml need to be updated with below command in the script Section:

- newman run FI_Stage_SmokeTests.json -e FI_environment_variables.json --reporters cli,htmlextra --reporter-htmlextra-export testReport.html

Note: To re execute the test cases in stage, contract needs to be deleted from the below tables: 
1. b2c_trustor_service_bank_data - b2c schema
2. seller_to_Contract - pos service
3. Investment_draft - Pos_service
4. Investment_id_mapping. - pos_service.
This is just to ensure same TIN is used for creation of New Contract