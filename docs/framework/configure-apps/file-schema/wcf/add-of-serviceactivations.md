---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850331"
---
# <a name="add-of-serviceactivations"></a>\<add> de \<serviceActivations>

Élément de configuration qui vous permet de définir des paramètres d’activation de service virtuel mappés à vos types de service Windows Communication Foundation (WCF). Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a>Syntaxe

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|usine|Chaîne qui spécifie le nom de type CLR de la fabrique qui génère un élément d'activation de service.|
|service|Le ServiceType qui implémente le service (Typename qualifié complet ou Typename court (s’il est placé dans le dossier App_Code).|
|relativeAddress|L'adresse relative dans l'application IIS active (par exemple « Service.svc ». Dans WCF 4,0, cette adresse relative doit contenir l’une des extensions de fichier connues (. svc,. xamlx,...). Aucun fichier physique ne doit exister pour relativeUrl|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Section de configuration qui décrit les paramètres d'activation.|

## <a name="remarks"></a>Remarques

L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.

Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application. Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle. En outre, `serviceHostingEnvironment` est une section pouvant être héritée machineToApplication. Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui-ci.

L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non-HTTP. Elle requiert des extensions dans relativeAddress, par exemple. svc,. xoml ou. xamlx. Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d’activer le service sur n’importe quelle extension. En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
