---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920032"
---
# <a name="add-of-serviceactivations"></a>\<Ajouter > de \<la > serviceActivations

Élément de configuration qui vous permet de définir des paramètres d’activation de service virtuel mappés à vos types de service Windows Communication Foundation (WCF). Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.

\<system.ServiceModel>\
\<serviceHostingEnvironment>

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
|factory|Chaîne qui spécifie le nom de type CLR de la fabrique qui génère un élément d'activation de service.|
|service|Le ServiceType qui implémente le service (Typename qualifié complet ou Typename court (s’il est placé dans le dossier App_Code).|
|relativeAddress|L'adresse relative dans l'application IIS active (par exemple « Service.svc ». Dans WCF 4.0 cette adresse relative doit contenir une des extensions de fichiers connues (.svc, .xamlx,…). Aucun fichier physique ne doit exister pour relativeUrl.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Section de configuration qui décrit les paramètres d'activation.|

## <a name="remarks"></a>Notes

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
