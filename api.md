# CodeJackRabbit TypeScript API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImZlMGYyMjU1OGZiNDM0MTEwODJkZjVlMDc2MmEyM2U5ZWFmOTBhOWM3MTNmZTRlZTljZmQyNzM3OTIyMjgwM2QiLCJvcGVyYXRpb25fY291bnQiOjIyLCJyZW5kZXJlciI6InR5cGVzY3JpcHQiLCJ2ZXJzaW9uIjoiMS40LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `fe0f22558fb43411082df5e0762a23e9eaf90a9c713fe4ee9cfd27379222803d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **verified**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new Client({ hooks })` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. `beforeRequest` is the one hook that may change the request (the documented per-request credential contract, which also reads credentials masked); the other three receive frozen `HookContext` copies.

`new Client({ tracer })` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `ComplianceGateRequest`
- `FileChange`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplQ29udHJhY3REcmlmdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCIsInBhdGgiOiIvdjEvYW5hbHlzaXMvY29udHJhY3QtZHJpZnQiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiIzYzJmZGFmOTM1MWUwZjYyMTQ0OWQ5NDA5NGQ1NjE5YzFiYTdiZGY5YzFhMDVjZDdmYzNkOWJiYzNkNTc5MTZkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjBlMTMyMTdlYmNmYjAxMDNhNmI3ZDFiNDJhYjRhMDk1NzA1NDFiN2JiZWU5ZTE5ZmVlOWQ3ZWEyZTg1NDgwZGMifQ -->
### `client.analysis.analyzeContractDrift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  

#### Signature

```typescript
client.analysis.analyzeContractDrift<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.analysis.analyzeContractDrift({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplUGVyZkZpbk9wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiI5OWY1NjQ0NWM2ZTdhNDEzYzJjMjZmYTc4MTQwMDljN2FhY2ZmZWYzMmMwNmZkOWViNDkxZTJkYWViNzRkZGUxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjdkZjI2N2RmZGQ5Yjc0NzFkM2QxODU1NjhjYTNhNmJmYTU0NTA0YTY5ZjA0NTJjNjZjZGFkYmVkOGViYTU2MmUifQ -->
### `client.analysis.analyzePerfFinOps`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  

#### Signature

```typescript
client.analysis.analyzePerfFinOps<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.analysis.analyzePerfFinOps({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5wbGFuU3RhY2tlZFByU3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6IjliZjFjMTNlZTgxOGJmNjcxNWIxMmNkM2Y4MGNmYmQxODkzMmQzNzg2MGMyNzBmM2NhMjU2MmVjYjAzNWM4YjAiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjk2MDA3MzAwNzE5M2ZiNzdmZGM4YTIwNTBmOTE0MTBiZjFiMDljMjAwMTQyMTVjMWI3ZDI1ZmFhNDA4MjRlOCJ9 -->
### `client.analysis.planStackedPrSplit`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  

#### Signature

```typescript
client.analysis.planStackedPrSplit<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.analysis.planStackedPrSplit({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

## Resource `analytics`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXRpY3MuZ2V0Um9pIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QW5hbHl0aWNzUm9pIiwicGF0aCI6Ii92MS9hbmFseXRpY3Mvcm9pIiwicmVzb3VyY2UiOiJhbmFseXRpY3MiLCJzZWN0aW9uX3NoYTI1NiI6ImEwN2Q1YTk4ZDhiMTU0MjRmYmY2MjM4MmYxYjIwN2Y1N2FmYjE1ZDMwOGFmMGM4MGVkZjNkNjk2MjkyNWM1NTEiLCJzaWduYXR1cmVfc2hhMjU2IjoiZThhOWNjZDA5YjIxOTQ3MDlhYzM2Mzk4ZmE0ZDBkMWI2MjVjNWVmNWM5MDEzNDhiYzg0MzNkMzg5MWY5MjAzMiJ9 -->
### `client.analytics.getRoi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  

#### Signature

```typescript
client.analytics.getRoi<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.analytics.getRoi();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

## Resource `capabilities`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjYXBhYmlsaXRpZXMuZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiZDYxYzQzM2EyOTdkODcyZjczYTAxYzY2OWJlMTQzZWJlOTFmZDZhNzZmYmIxMWQwOWE2MjM3MzI3NTMzYzA3NiIsInNpZ25hdHVyZV9zaGEyNTYiOiI2NDZiM2I2ZWFjNGQwZDM4MWZjNzJkZmZlYmZmM2Y5NTY5M2I1ZjAwM2Q2MTUxYjFhMTU2Yjk0NzI2Yzg1N2E4In0 -->
### `client.capabilities.get`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  

#### Signature

```typescript
client.capabilities.get<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.capabilities.get();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

## Resource `compliance`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV2YWx1YXRlR2F0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL2dhdGUiLCJyZXNvdXJjZSI6ImNvbXBsaWFuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjJjODAzYjNiOTI0MTYxZGYzZDczMzNlMjM4M2RlNWZjY2RjNzc5NjU3YzQyYTNiYWRhNTE2M2NjNmY3ODFlOTIiLCJzaWduYXR1cmVfc2hhMjU2IjoiMzk0ODI3YmI5YjUwMWI4YTEwMmE5MDM3OWRhN2M0ZjJlZjhiOTBiNDMyYzNjZjhlYzY0NGY0Yjg4MDQ2MjVhNSJ9 -->
### `client.compliance.evaluateGate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  

#### Signature

```typescript
client.compliance.evaluateGate<Raw extends boolean = false>(body: ComplianceGateRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.compliance.evaluateGate({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV4cG9ydFNhcmlmIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImV4cG9ydFNhcmlmIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL3NhcmlmIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJhNDNjMzZhMGQyZTI1MjllY2RmMDkzYzM4N2M3MWFmNGE3MmNjNWFjOGQyYWM3MmY4NTRhYzZjYmMxMGRkNDJiIiwic2lnbmF0dXJlX3NoYTI1NiI6IjVmMTMwNWVlNDE2ZTA1ZTczMWU2NjMwMWQyYWQ3ODkwYjEyMjNjZDkwNjdlZmU1NmZlZmNjZTVjOTFhOTg2NjQifQ -->
### `client.compliance.exportSarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  

#### Signature

```typescript
client.compliance.exportSarif<Raw extends boolean = false>(body: Record<string, unknown>, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.compliance.exportSarif({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiMzExNWJiYjAwYWVkYmRlNmY2ZjU1Y2VlMDQ3ZjljYWM0MGU4ODQyNmRkOWEwMDM4NGQ3M2FiNTUzMzJlODg0NCIsInNpZ25hdHVyZV9zaGEyNTYiOiJlYTliN2Q3YTJjYzBlYWMzMjkyYWFkZjQwODRmZDY5ODg4N2E3NjFkZDEzMmZhYTI2OWJhZDlhNzgxYmExY2M4In0 -->
### `client.health.get`

Operation ID: `getHealth`  
Route: `GET` `/health`  

#### Signature

```typescript
client.health.get<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.health.get();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `reviews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmJ1aWxkQXV0b2ZpeEJ1bmRsZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUiLCJwYXRoIjoiL3YxL3Jldmlld3MvYXV0b2ZpeCIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiNmIyOGNhMzBmZGRmOTE1OTBhMTMwOTVjOWQ4ZWI5Njg5ZTcwNmNmYzk1MDkzYjcyYzQ3OWI5M2Y1MDc2YzA2NCIsInNpZ25hdHVyZV9zaGEyNTYiOiIyMjVjYmFjMmEwOGI2ZTYzMGZlZmU4ZWEwMzY0N2VlYzAzZjJhZDU4OThmNTY1MmQ0MDc3NGZhMzRmNzliNWVmIn0 -->
### `client.reviews.buildAutofixBundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  

#### Signature

```typescript
client.reviews.buildAutofixBundle<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.reviews.buildAutofixBundle({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNvbXB1dGVSaXNrUmFkYXIiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29tcHV0ZVJpc2tSYWRhciIsInBhdGgiOiIvdjEvcmV2aWV3cy9yaXNrLXJhZGFyIiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiI0MzAxMGFkMTYzNDM5Y2I0Nzk1NzA2YTQ2MjI5NjNmZmE5NDc1ZDdlYzBmMTUzOTFjN2E3YmQ3ZWQ0MTVmMjU0Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjQwNmJiNWUzMTcxMjhkNmJlNWJjNWRkZTIxYzViMDZjNjZkOWNhN2QzODBjNTJmY2RjNmI2MDdkZTNmZjU4NmUifQ -->
### `client.reviews.computeRiskRadar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  

#### Signature

```typescript
client.reviews.computeRiskRadar<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.reviews.computeRiskRadar({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNyZWF0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6ImZmZmYxZjk4NDYyMTk5OTY2MDJlZWQyNmM4Y2JmMTc4NmJmNzQ1OTgyMGEwZDU2YjJmMjZjMWQ4MjBkZTEwMzUiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmRhYjdkYTc2MGMzNzY0ZDA0ZjQ0MzA0MzNlMWJjNzBkNzI4MjFlODQ1ZTRiNDg0MjhkNjBjMWRiMGU5OTQ3NSJ9 -->
### `client.reviews.create`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  

#### Signature

```typescript
client.reviews.create<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.reviews.create({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

## Resource `saas`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmZpbmFsaXplTWV0ZXJpbmdRdW90YSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvZmluYWxpemUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjhlNDRkMTk2MTNmMmI1ZmQ3ZWE1NGNlNDE0OTFmZDRkNWQ5YjJjZmQ1ZTk5MDAzMzY1YmExYTU4YTE1YWNiYzUiLCJzaWduYXR1cmVfc2hhMjU2IjoiZTE5NjM2ZGZkYTdiMTQyMjFiOGI0MzA2MDk3NzFmMWYzN2JlMjJkZTQ3NTI3YmMxYzcxNGJkZDEyNjE3NGQ5YSJ9 -->
### `client.saas.finalizeMeteringQuota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  

#### Signature

```typescript
client.saas.finalizeMeteringQuota<Raw extends boolean = false>(body: Record<string, unknown>, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.saas.finalizeMeteringQuota({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmdldEJsdWVwcmludCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFNhYXNCbHVlcHJpbnQiLCJwYXRoIjoiL3YxL3NhYXMvYmx1ZXByaW50IiwicmVzb3VyY2UiOiJzYWFzIiwic2VjdGlvbl9zaGEyNTYiOiJjN2RhYzZkM2FiNDE3NWNlZGI0OTQxMDQ2MGZkNTQxZmYxODJhNGExNTY4Mzc0NDc1Y2Q5YWUwNjcyOWY5MTFlIiwic2lnbmF0dXJlX3NoYTI1NiI6ImU0NDQ5YmZhZDQwM2FmOTllYTNmMjgzNzFiODY1NmZmMWQ4N2M0MTg2OTcwZjg3YzUzNDQ5ZDcwMDI5MjAyYmYifQ -->
### `client.saas.getBlueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  

#### Signature

```typescript
client.saas.getBlueprint<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.saas.getBlueprint();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmlzc3VlU3VyZmFjZUxlYXNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Imlzc3VlU3VyZmFjZUxlYXNlIiwicGF0aCI6Ii92MS9zYWFzL3N1cmZhY2UtbGVhc2UvaXNzdWUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjAxMzcxNTA3Y2IwM2RhMjI2NTNmMmYxZmQzNmU1NDBhMmM0NzVkYzRkODE5NWNjNjA0YTE3YjhlZWVlZGI3OTgiLCJzaWduYXR1cmVfc2hhMjU2IjoiNGQ0MDY5NzU0OGVhNmZhM2UwZmViM2JmM2I1NDJmMGExODkzMDQzOWQ1YTEzMGI0ZjVhZTc1MjAxYTQxOGNjZSJ9 -->
### `client.saas.issueSurfaceLease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  

#### Signature

```typescript
client.saas.issueSurfaceLease<Raw extends boolean = false>(body: Record<string, unknown>, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.saas.issueSurfaceLease({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLnJlc2VydmVNZXRlcmluZ1F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlc2VydmVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL3Jlc2VydmUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjNhNDI5NDY0NzQxYmZjNjFhMzZmYTg4NWUxODFiZTUzODcxM2E3NmRjNjk5NmRjZWU5MTdlZGNiZjZkMDUzZDAiLCJzaWduYXR1cmVfc2hhMjU2IjoiZTcyOTE4OGFkMzkyZDlkMDNmNjJhOWU0N2I4NGQwYWUxMWFjOGI1ZGNmODQ1ZTU0MWM5ZTNlY2NiMGI0MjFjZCJ9 -->
### `client.saas.reserveMeteringQuota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  

#### Signature

```typescript
client.saas.reserveMeteringQuota<Raw extends boolean = false>(body: Record<string, unknown>, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.saas.reserveMeteringQuota({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

## Resource `sbom`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYm9tLmdlbmVyYXRlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImdlbmVyYXRlU2JvbSIsInBhdGgiOiIvdjEvc2JvbSIsInJlc291cmNlIjoic2JvbSIsInNlY3Rpb25fc2hhMjU2IjoiNjUxOTcyZDU4YWVkNjFjNjA3ZmUzNmYwYjg2NDk1ZTk1YmYzZTJlYzAzMzUwZGQ2NWY1Njc4MWExNzI4MGM3MCIsInNpZ25hdHVyZV9zaGEyNTYiOiI0MmMyODc4NGJlMGNiOGRjNDY1Mzg0MWY4NzljMGM3YTY3ZTkzMWQ3MWZjNzYzZDNkODFiZDg3NmZhYmUyMTQyIn0 -->
### `client.sbom.generate`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  

#### Signature

```typescript
client.sbom.generate<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.sbom.generate({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

## Resource `supplyChain`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzdXBwbHlDaGFpbi5hbmFseXplIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVTdXBwbHlDaGFpbiIsInBhdGgiOiIvdjEvc3VwcGx5LWNoYWluL2FuYWx5emUiLCJyZXNvdXJjZSI6InN1cHBseUNoYWluIiwic2VjdGlvbl9zaGEyNTYiOiJhZTU3MTM2MWNlNTIyYzU4MTlmZThjYzBiOWI2Y2ExYzQ1MzFmMTY3OWJjMmQ1Y2U3MDZmOTBiZTMyOGM3YWI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6Ijc2M2Y4MDk0YzRjMTc2YjNkMzE3ZTRjMjY2MzVmOTIwODRlMjcxMTdhNjc3NDQ4YjM5M2M0NWEyZjVlZGY5NTgifQ -->
### `client.supplyChain.analyze`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  

#### Signature

```typescript
client.supplyChain.analyze<Raw extends boolean = false>(body: ReviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.supplyChain.analyze({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

## Resource `tasks`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5jcmVhdGVDb2RpbmciLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ29kaW5nVGFzayIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiIwNDFmYzJlZDFlMjg5ZDBjMDNhMjk5YjgyZDg4MTQyM2YyOTI3NjQxOTcxMTVhYmM0NDdhYTMxNmEwZTI1ZWI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImRjOGRlZDhjNjRlMmRjOTMzNTc0MGI1OGQ4MjNjOTc1NzRmMzczYmZhMTZmZDA1MTQ2NGY5ODgxZDgxZTFiMzkifQ -->
### `client.tasks.createCoding`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  

#### Signature

```typescript
client.tasks.createCoding<Raw extends boolean = false>(body: Record<string, unknown>, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.tasks.createCoding({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5saXN0Q29kaW5nIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdENvZGluZ1Rhc2tzIiwicGF0aCI6Ii92MS90YXNrcyIsInJlc291cmNlIjoidGFza3MiLCJzZWN0aW9uX3NoYTI1NiI6ImMyNTgwY2E4YWVmYjA1YTEzYzY4MjA0MzhkYTY4OTE2YWYwMWJhOGNlNGRlYzc0OGU1NTM5MDlkNzU0MDIwN2MiLCJzaWduYXR1cmVfc2hhMjU2IjoiZWQ1OTI5NjVlYmJmMjUxNDFmYTNlOTA2NjIyOGE3Y2VlYjNiOTJlOGE3YjY2ZjdmNTdjYjZmODNjNjMxMTBiYiJ9 -->
### `client.tasks.listCoding`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  

#### Signature

```typescript
client.tasks.listCoding<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.tasks.listCoding();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

## Resource `triage`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0cmlhZ2UuZ2V0UXVldWUiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSIsInBhdGgiOiIvdjEvdHJpYWdlIiwicmVzb3VyY2UiOiJ0cmlhZ2UiLCJzZWN0aW9uX3NoYTI1NiI6IjYyMWVmYzNmM2EwOTU4M2E1YTVmNmJiNDNlYmM2ZDU0ODk2OWQ0NmE1MDUzNTVlZDg1Y2Y3ZjFhNzVlODY1OTUiLCJzaWduYXR1cmVfc2hhMjU2IjoiOGVhZGRkZjAyMWI2ZDhhZGJiMTRiYjBhNjI1OTUyZTU3MjY1YTQ4YmFhNGIyN2NkMzUwYzg5OGU0YTg1YmExZiJ9 -->
### `client.triage.getQueue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  

#### Signature

```typescript
client.triage.getQueue<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.triage.getQueue();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6ImYwMmViYmRiYmVhZGY4OThlMDBlNWE1NGYzZGZiMWJmOTQ1OWI2MTY3ODlmMThiMmZjOWQ3MzQ2NzEzM2M3NDQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMWZlYmY5ZjBmNTc1NTdlNWI4MDMzNTllMzllYTJlODU4Y2M0ZGU4ZmMyNjg4OGQxZTMwMmM3M2E2N2NjM2MxZCJ9 -->
### `client.waitlist.list`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  

#### Signature

```typescript
client.waitlist.list<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.waitlist.list();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6ImI4YjZkYmY1MjJkNDgyMzhmODUxOGZiNjEzMDM2ZWFlYWY2ZTE1MGNiZTVhYTljY2UwMjdkODE0ZTlmNjk5NmIiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjExZGQ2ODBiMzZlMDZiMGVjYTZmOWI2OTA4YWE0M2IxYzYyOWQyOGEwZGQ1ZjRmNzc1MGZkYTI4Mzg1NzQ5ZCJ9 -->
### `client.waitlist.register`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  

#### Signature

```typescript
client.waitlist.register<Raw extends boolean = false>(body: WaitlistRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<undefined> : undefined>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.waitlist.register({"email": "example-c65f@example.test"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->

