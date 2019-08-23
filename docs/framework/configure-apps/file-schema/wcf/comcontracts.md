---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919474"
---
# <a name="comcontracts"></a>\<comContracts>
La section de configuration `comContracts` contient des éléments qui vous permettent de spécifier différentes propriétés d'un contrat de service d'intégration COM+.  
  
## <a name="specifying-namespace-and-contract"></a>Spécification d'espace de noms et de contrat  
 Les contrats de service d’intégration com+ sont actuellement `http://tempuri.org` restreints à l’espace de noms et le nom de contrat est dérivé de l’interface com de prise en charge. Toutefois, vous pouvez en spécifier d'autres à l'aide de la section `comContracts` du fichier de configuration.  
  
 Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l’espace de noms et le nom du contrat de service, aussi bien qu’une option pour mettre en vigueur l’utilisation sur les liaisons de session.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.  
  
 Lorsque cette section est vide, l'initialisation de service applique un espace de noms et un nom de contrat par défaut à partir de l'ID d'interface COM de prise en charge.  
  
 En outre, vous pouvez utiliser l' [ \<élément ExposedMethod >](exposedmethod.md) pour spécifier les méthodes com+ exposées lorsque l’interface sur un composant com+ est exposée en tant que service Web. Vous pouvez également utiliser l' [ \<> persistableTypes](persistabletypes.md) pour spécifier les types persistants utilisés dans l’intégration. Enfin, vous pouvez utiliser l' [ \<élément UserDefinedType >](userdefinedtype.md) pour inclure les types définis par l’utilisateur (UDT) qui doivent être inclus dans le contrat de service.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [Intégration à des applications COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Guide pratique : Configurer les paramètres du service COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
