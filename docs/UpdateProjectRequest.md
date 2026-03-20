

# UpdateProjectRequest

Fields to update on a project (name, description, logoUrl, settings, auth).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  [optional] |
|**description** | **String** |  |  [optional] |
|**logoUrl** | **URI** | Public URL for the project logo/brand image. Prefer uploading via **POST /api/projects/{id}/logo** or **POST /api/projects/{orgId}/projects/{id}/logo** (stored under logo/project/ in platform storage). Used in project-related emails.  |  [optional] |
|**settings** | [**ProjectSettings**](ProjectSettings.md) |  |  [optional] |
|**auth** | [**AuthConfig**](AuthConfig.md) |  |  [optional] |



