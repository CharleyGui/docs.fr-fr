---
title: Schéma de configuration WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 44d5e0acc6f5a9ca43949bce0c7964354ad18270
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573655"
---
# <a name="wcf-configuration-schema"></a>Schéma de configuration WCF

Les éléments de configuration Windows Communication Foundation (WCF) vous permettent de configurer des applications clientes et de service WCF. Vous pouvez utiliser l’[outil Éditeur de configuration (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier des fichiers de configuration pour les clients et les services. Les fichiers de configuration étant au format XML, il est nécessaire de maîtriser ce format pour pouvoir modifier ces fichiers à l'aide d'un éditeur de texte, sans quoi vous risquez de rencontrer des problèmes tels qu'une balise ou un attribut d'élément XML manquant. Ce problème a lieu car les étiquettes et les attributs d’éléments XML respectent la casse.  
  
 Le système de configuration WCF est basé sur l' <xref:System.Configuration> espace de noms. Par conséquent, vous pouvez utiliser toutes les fonctionnalité standard fournies par l’espace de noms <xref:System.Configuration>, tel que le verrouillage, le chiffrement et la fusion de la configuration, afin de renforcer la sécurité de votre application et sa configuration. Pour plus d'informations sur ces concepts, consultez les rubriques suivantes :  
  
 [Chiffrement des informations de configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Verrouillage des paramètres de configuration](/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 Cette section décrit toutes les valeurs possibles de chaque élément de configuration et leur interaction avec d'autres éléments de configuration WCF. La carte suivante illustre le schéma de configuration WCF :

:::image type="content" source="./media/index/windows-communication-foundation-configuration-schema.gif" alt-text="Diagramme qui montre le schéma de configuration WCF." lightbox="./media/index/windows-communication-foundation-configuration-schema.gif":::
  
> [!CAUTION]
> Protégez les sections de configuration WCF dans vos fichiers de configuration d’application (app.config) avec des listes de Access Control (ACL) appropriées afin d’éviter toute menace potentielle pour la sécurité. Par exemple, assurez-vous que seules les personnes appropriées peuvent accéder ou modifier les paramètres de sécurité sur les liaisons d’application ou la section du modèle de service du fichier de configuration pour un service.  
  
## <a name="in-this-section"></a>Dans cette section  

 [\<system.serviceModel>](system-servicemodel.md)  
 Décrit l'élément `ServiceModel`.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 Configure l'outil SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 Élément de niveau supérieur permettant de définir les options lors de l'utilisation de sérialiseurs tels que le <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Sections connexes  

 [Configuring Windows Communication Foundation Applications](../../../wcf/configuring-services.md)  
 Décrit comment configurer les clients et les services WCF.
