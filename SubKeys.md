# []string value compresion format []string

- these are reccommended subkeys for app planning systems
- used to compress subkeys to simplify yaml for LLM operations
- is also a method of compressing complex json
- only need to use values when relevant and exclude when not relevant
- these are examples, but can have any logical value that aligns with intent
  
##

## external_services.service []

```
endpoint:<local-ref>
method:<verb>
path:<path>
protocol:<proto>
direction:<dir>
auth:<scheme>
scopes:<csv>
request:<schema>
response:<schema>
payload:<schema>
status_codes:<csv>
rate_limit:<rpm>
idempotent:<bool>
timeout_ms:<int>
retry_policy:<policy>
content_type:<mime>
endpoint_url:<url>
endpoint_env:<env-var>
spec_ref:<global-ref>
version:<semver> 
Event-specific endpoints add: delivery:<at_most_once|at_least_once|exactly_once>, signature:<hmac_sha256|ed25519|none>, dead_letter:<bool>.
File-upload endpoints add: max_size_mb:<int>, allowed_mime:<csv>, chunked:<bool>.
```

## secrets_provider ""

```
provider:<type>
scope:<scope>
rotation:<mode>
region:<region>
namespace:<ns>
fallback:<provider>
```

## domain-entities-and-relations: []

```
Core subkeys:
entity:<Name>
owned_by:<microservice>
storage_ref:<store>
tenant_scoped:<bool>
soft_delete:<bool>
audited:<bool>

Attribute subkeys:
attr:<Entity>.<field>:<type>
nullable:<bool>
unique:<bool>
indexed:<bool>
default:<value>
validation:<rule> — email|url|regex:<pattern>|range:<min-max>|length:<min-max>|enum:<values>.
pii:<bool>
encrypted_at_rest:<bool>
max_length:<int>
format:<format>

Relation subkeys:
rel:<Entity>.<kind>:<Other>
cardinality:<1-1|1-n|n-1|n-n>
cascade:<mode>
foreign_key:<field>
join_table:<name>
lazy_load:<bool>
```

## integrations: []


```
Core subkeys:
from:<source>, to:<dest>
type:<sync|async>
protocol:<proto>
direction:<dir>
category:<cat>
env_url_binding:<var name>

External-linkage subkeys (when to is external):
external_service:<name>
endpoint_spec_ref:<ref>

Connection subkeys:
endpoint:<url>
endpoint_env:<env>
auth:<scheme>

Resilience subkeys:
timeout_ms:<int>
retry_policy:<policy>
circuit_breaker:<bool>
rate_limit:<rpm>

Observability subkeys:
idempotency_key:<header>
correlation_id:<header>
trace_propagation:<bool>

Event-specific:
event_name:<name>, topic:<name>, delivery:<guarantee>.
```

## storage: []


```
Core subkeys:
store:<ref>
category:<category>
type:<db_type>

Connection subkeys:
endpoint:<url>
endpoint_env:<env>

Ownership and access subkeys:
owner:<microservice>
readers:<csv>
writers:<csv>
entities:<csv>

Operational subkeys:
tenant_isolation:<mode>
encryption_at_rest:<bool>
backup:<policy>
ha:<mode>
replicas:<int>

Content subkey:
purpose:<text>

Model subkey:
model:[ <prefix>: <value>; ... ]
```

## flows: []


```
flow:<ref>
trigger:<trigger>
actor:<actor>
initiator:<source>
terminator:<dest>
sync:<bool>
sla_ms:<int>
step:<description>
implements_acceptance:<csv>
implements_workflow:<csv>
```

## constraints: []


```
constraint:<ref>
kind:<security|compliance|nfr>
scope:<scope>
severity:<must|should|may>
measurable:<bool>
metric:<name>.
threshold:<value>
applies_to:<csv>
body:<verbatim-text>
```

## design: []


```
Visual common factors (token entries) subkeys:
token:<name>
kind:<kind>
value:<literal>
scope:<scope>
mode:<mode>
consumes:<csv>
derives_from:<token-ref>
a11y_role:<role>

Interaction/UX patterns (pattern entries) subkeys (Track B — interaction/UX patterns):
pattern:<ref>
kind:<kind>
applies_to:<target>
value:<option>
mode:<mode>
consumes:<csv>
implements_a11y:<csv>

File-specific compositions (composition entries) subkeys 
composition:<ref>
scope:<scope>
description:<text>
references_tokens:<csv>
references_patterns:<csv>
mode:<mode>

Accessibility requirements (a11y entries):
a11y:<ref>
kind:<kind>
scope:<scope>
standard:<standard>
criterion:<criterion-ref>
requirement:<text>
measurable:<bool>
metric:<name>
threshold:<value>
verified_by:<pattern-ref or composition-ref>

Component API surface (component entries):
component:<ref>
kind:<kind>
variants:<csv>
sizes:<csv>
states:<csv>
slots:<csv>
aria_role:<role>
css_vars_prefix:<prefix>
theming_hooks:<csv>
implements_patterns:<csv>
implements_a11y:<csv>
consumes:<csv>

Brand positioning (brand entries):
brand:<ref>
core_idea:<text>
taglines:<csv>
voice_tone:<text>
imagery_themes:<csv>
imagery_treatments:<csv>
iconography_style:<pattern-value>
alt_text_pattern:<text>
clear_space_rule:<text>
consumes:<csv>
```

## assets: []


```
Core subkeys:
asset:<ref>
path:<path>
kind:<kind>
mime:<mime>
serves:<csv>

Placement subkeys:
placement:<placement>

Usage subkeys (composed as semicolon-separated inner grammar, matching your existing usage: pattern):
render:<mode>
font-family:<name>
font-weight:<range>
font-style:<style>
alt:<text>
lazy:<bool>
preload:<bool>
breakpoint:<min-max>
aspect_ratio:<w:h>
object_fit:<mode>

Distribution subkeys:
source:<source>
cdn_url:<url>
bundled_at:<time>
variants:<csv>
dimensions:<wxh>
responsive:<csv>

Legal subkey:
license:<license-ref>

Accessibility subkey:
alt:<text>

Descriptive subkey:
purpose:<text>
```

