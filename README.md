# Zerops x GO
This is the most bare-bones example of GO app running on Zerops.

![go](https://github.com/zeropsio/recipe-shared-assets/blob/main/covers/svg/cover-go.svg)

## Deploy on Zerops
You can either click the deploy button to deploy directly on Zerops, or manually copy the [import yaml](https://github.com/zeropsio/recipe-go/blob/main/zerops-project-import.yml) to the import dialog in the Zerops app.

[![Deploy on Zerops](https://github.com/zeropsio/recipe-shared-assets/blob/main/deploy-button/green/deploy-button.svg)](https://app.zerops.io/recipe/go)

<br/>
<br/>

## Recipe features
- **Golang v1.22.** on **Zerops GO** service
- Zerops **PostgreSQL 16** service as database
- Healthcheck setup example
- Utilization of Zerops' built-in **environment variables** system
- Utilization of Zerops' built-in **log management**

## Production vs. development

Base of the recipe is ready for production, the difference comes down to:

- Use highly available version of the PostgreSQL database (change *mode* from *NON_HA* to *HA* in recipe YAML, *db* service section)
- Use at least two containers for the GO service to achieve high reliability and resilience (add *minContainers: 2* in recipe YAML, *api* service section)

Further things to think about when running more complex, highly available GO production apps on Zerops:

- Containers are volatile - use Zerops object storage to store your files
- Use Zerops Redis (KeyDB) for caching, storing sessions and pub/sub messaging
- Use more advanced logging lib, such as [Logrus](https://github.com/sirupsen/logrus), [Zap](https://github.com/uber-go/zap) or [ZeroLog](https://github.com/rs/zerolog)