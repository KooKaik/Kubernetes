# TP Kubernetes

## Notion CRD

Un CRD (**C**ustom **R**esource **D**efinition) est un objet qui nous permet de définir une Custom Resource.
C'est un outil qui très interressant pour améliorer les capacités de base de notre Kubernetes ainsi le rendre plus puissant.

Une Custom Ressource nous permet de créer notre propre "kind" et donc d'étendre les capacités de Kubernetes en ajoutant de nouveau kind à notre Kubernetes permettant d'integrer des nouvelles API utile pour notre application.

**Exemple d'un CRD**

```
apiVersion: apiextensions.k8s.io/v1beta1
kind: CustomResourceDefinition
metadata:
  name: appconfigs.stable.example.com
spec:
  group: stable.example.com
  versions:
    - name: v1
      served: true
      storage: true
  scope: Namespaced
  names:
    plural: appconfigs
    singular: appconfig
    kind: AppConfig
    shortNames:
    - ac
```

## Répartition des namespaces

Dans notre TP Kubernetes, nous avons 3 namespaces:
- database (contient toutes les configuration pour notre base de données)
- web (contient toutes les configuration pour les applications web dont Wordpress)
- monitoring (contient toutes les configuration pour le monitoring avec Prometheus)

Les namespaces permettent d'isoler nos différents services.