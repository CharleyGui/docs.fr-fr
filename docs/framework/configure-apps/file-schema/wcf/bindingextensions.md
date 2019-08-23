---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 34ba198de33ae4aa1882d13f74bd2d538999a0c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919790"
---
# <a name="bindingextensions"></a>\<bindingExtensions>
Cette section active l’utilisation d’une liaison définie par l’utilisateur à partir d’un ordinateur ou d’un fichier de configuration de l’application. Vous pouvez ajouter une liaison définie par l'utilisateur à cette collection en utilisant le mot clé `add` et affecter à l'attribut `type` de l'élément une liaison définie par l'utilisateur, aussi bien que l'attribut `name` au nom de la liaison définie par l'utilisateur.  
  
 Les extensions de liaison permettent à l'utilisateur de créer des liaisons qu'il définit lui-même pour les utiliser dans le cadre d'une configuration de point de terminaison. Par programme, une extension de liaison est un type qui implémente la classe abstraite <xref:System.ServiceModel.Channels.Binding>.  
  
 L'exemple suivant utilise l'élément `add` ainsi que l'attribut `name` pour ajouter une extension de liaison à la section `bindingElementExtensions` du fichier de configuration.  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Pour ajouter des capacités de configuration à l'élément, l'utilisateur doit écrire et enregistrer un élément `bindingSection`. Pour plus d'informations, consultez la documentation <xref:System.Configuration>.  
  
 Après la définition de l’élément et de son type de configuration, l’extension peut être utilisée comme une partie du point de terminaison comme présenté dans l’exemple suivant.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Voir aussi

- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
