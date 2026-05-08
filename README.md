# OpenAppIntent Format

- Intent Driven Devlopment Yaml Spec
- For Service Level Intent Driven Devlopment
  
## Base Format

```
service_name: ""
spec_version: "1.0.0"
description: ""
acceptance: []
constraints: []
runtime:
  language: ""
  language_version: ""
  middleware: []
deployment_targets:
  - { name: "", platform: "k8s|ios_store|android_store|lambda|vm", region: "", replicas: 0 }
user_workflows: 
  - workflow: ""
    steps: [""]
  - workflow: ""
    steps: [""]
auth:
  tenancy_model: "single_tenant|multi_tenant|hybrid"
  schemes:
    - scheme_ref: "" 
      type: "oidc|bearer_jwt|api_key|session_cookie|mtls|none"
      provider: "auth0|internal|cognito" 
      oidc:  
        issuer: "" 
        audience: "" 
        flow: "authorization_code|client_credentials|device_code" 
        scopes: ["openid", "profile", "email"] 
  authorization:
    model: "rbac|abac|scopes|none"  
    roles: []
depends_on_external_services: []   
secrets_provider: []  
integration_contexts:
  - description: ""
    direction: "exposes|consumes"
    category: "api_communication|data_retrieval_and_aggregation|authentication_and_authorization|realtime_and_streaming_communication|event_driven_interaction|file_upload_download|direct_low_level_communcation"
    type: "rest|graphql|grpc|websocket|webhook|sse|webrtc|kafka|rabbitmq|sqs|sns|nats|redis_pubsub|mqtt|amqp|s3|ftp|sftp|multipart_http|tcp|udp|unix_socket|shared_memory"
    methods: []
    path: ""
    event_name: ""
    auth:
      scheme_ref: ""  
      required_roles: [] 
      required_permissions: []
    content_type_request: ""
    content_type_response: ""
    request_body_schema: {}
    response_body_schema: {}
    http_status_codes: []
    error_responses: []
    requested_by: []
    requested_from: []
storage:  
  database_contexts:  
    - name: ""
      category: "relational|document|key_value|wide_column|graph|vector|multi_model|ledger|time_series|spatial|blockchain|version_control|file_operation"
      database_type: ""
      host: ""
      port: 0
      database: ""
      user_env: ""
      password_env: ""
      sslmode: ""
      parameters": {}
      models:
        - { key_name: "", key_type: "table|collection|bucket|keyspace|node|table|serie|layer|chain|version_control|file_operation", values: [] }
  version_control:
    - { name: "", repo_type: "", repo_path: "", default_branch: "", access_transport: "", access_type: "", scopes: [], allowed_operations: [] }
  file_storage:
    - { name: "", backend: "local_fs|nfs|object_storage|artifact_store|provider_repo_files_api", root: "", bucket: "", prefix: "" }
domain-entities-and-relations:
  - entity: ""
    owned_by: ""
    storage_ref: ""
    tenant_scoped: true
    soft_delete: true
    audited: true
    attributes:
      - { field: "", type: "", unique: , indexed:  }
    relations:
      - { has_many: "", fk: "", cascade: "" }
design:
  tokens:
    - { token: "", kind: "", value: "" }
  patterns:
    - { pattern: "",   kind: "", value: "", applies_to: "" }
  compositions:
    - composition: ""
      scope: ""
      description: ""
      rferences_tokens: ""
      references_patterns: ""
  a11y:
    - { a11y: "", kind: "", scope: "", standard: "", level: "", criterion: "1.4.3", metric: "", threshold: 0.0, requirement: "", verified_by: "" }
  components:
    - component: ""
      kind: ""
      variants: ""
      sizes: ""
      states: ""
      slots: ""
      aria_role: ""
      css_vars_prefix: ""
      implements_patterns: ""
      implements_a11y: ""
assets:
  - { asset: "", path: "", kind: "", mime: "", placement: "", render: "", alt: "", dimensions: "",  source: "", variants: "", purpose: "" }
```

## External Service Index 

```
external_service_name: ""
description: ""
```

## External Service Value

```
external_service_name: ""
spec_version: "1.0.0"
description: ""
endpoints:
  - { name: "", base_url: "", region: "" }
auth:
  tenancy_model: "single_tenant|multi_tenant|hybrid"
  schemes:
    - scheme_ref: "" 
      type: "oidc|bearer_jwt|api_key|session_cookie|mtls|none"
      provider: "auth0|internal|cognito" 
      credential_storage:
        kind: "env|secret_manager|vault" 
        name: "" 
      oidc:  
        issuer: "" 
        audience: "" 
        flow: "authorization_code|client_credentials|device_code" 
        scopes: ["openid", "profile", "email"] 
      hmac:  
        secret_ref: ""
        signature_header: ""
        algorithm: ""
  authorization:
    model: "rbac|abac|scopes|none"  
    roles: []
rate_limits:
  - { endpoint: "", limit: "", window: "", on_breach: "" }  
integration_contexts:
  - description: ""
    direction: "exposes|consumes"
    category: "api_communication|data_retrieval_and_aggregation|authentication_and_authorization|realtime_and_streaming_communication|event_driven_interaction|file_upload_download|direct_low_level_communcation"
    type: "rest|graphql|grpc|websocket|webhook|sse|webrtc|kafka|rabbitmq|sqs|sns|nats|redis_pubsub|mqtt|amqp|s3|ftp|sftp|multipart_http|tcp|udp|unix_socket|shared_memory"
    methods: []
    path: ""
    event_name: ""
    auth:
      scheme_ref: ""  
      required_roles: [] 
      required_permissions: []
    content_type_request: ""
    content_type_response: ""
    request_body_schema: {}
    response_body_schema: {}
    http_status_codes: []
    error_responses: []
    requested_by: []
    requested_from: []
```


