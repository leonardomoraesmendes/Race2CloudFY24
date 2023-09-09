## CD Automatizado Mediante ArgoCD en Cluster OKE

## ##

### Requerimientos:

- Cuenta de Oracle Cloud Infrastructure(test gratuito https://www.oracle.com/cloud/free/)
- Cuenta de Github (https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)

### ¿Qué vamos a hacer?

- Clonar repositorio GitHub
- Configurar OKE
- Desplegar aplicación mediante ArgoCD

### Paso a Paso

0. Crear Compartment
	Menu > Identity & Security > Compartmente > New Compartment
	```
	CAMPO				VALOR
	==============================================
	Name		 		OKE
	Description 			OKE
	Parent Compartment 		XXXXX (root)

1. Crear Cluster 

....

1. Posterior a la creación del cluster OKE, acceder a este
	Menu > Developer Services > Kubernetes Clusters (OKE) > Clustyer creado
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/af8781b0-f2fa-4575-97ff-a6705f171d20)

