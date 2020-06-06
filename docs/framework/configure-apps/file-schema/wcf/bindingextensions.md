---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039144"
---
# \<bindingExtensions>

Cette section active l’utilisation d’une liaison définie par l’utilisateur à partir d’un ordinateur ou d’un fichier de configuration de l’application. Vous pouvez ajouter une liaison définie par l'utilisateur à cette collection en utilisant le mot clé `add` et affecter à l'attribut `type` de l'élément une liaison définie par l'utilisateur, aussi bien que l'attribut `name` au nom de la liaison définie par l'utilisateur.

Les extensions de liaison permettent à l'utilisateur de créer des liaisons qu'il définit lui-même pour les utiliser dans le cadre d'une configuration de point de terminaison. Par programme, une extension de liaison est un type qui implémente la classe abstraite <xref:System.ServiceModel.Channels.Binding>.

L’exemple suivant utilise l' `add` élément, ainsi que l' `name` attribut pour ajouter une extension de liaison à la `bindingExtensions` section du fichier de configuration :

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

Après la définition de l’élément et de son type de configuration, l’extension peut être utilisée dans le cadre d’un point de terminaison, comme indiqué dans l’exemple suivant :

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
