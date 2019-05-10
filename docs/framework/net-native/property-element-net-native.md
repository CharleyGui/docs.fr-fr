---
title: <Property> Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 374ace4ec5e25731e4a7e958be145a660ff2ef7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614865"
---
# <a name="property-element-net-native"></a>\<Propriété >, élément (.NET Native)
Applique la stratégie de réflexion runtime à une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom de la propriété.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur la propriété ou l'énumération de celle-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à la propriété au moment de l'exécution pour autoriser la programmation dynamique. Grâce à cette stratégie, une propriété peut être définie ou récupérée dynamiquement au moment de l'exécution.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès à une propriété au moment de l'exécution pour permettre aux instances de type d'être sérialisées par des bibliothèques, telles que le sérialiseur JSON Newtonsoft, ou d'être utilisées pour la liaison de données.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Value|Description|  
|-----------|-----------------|  
|*nom_méthode*|Nom de la propriété. Le type de la propriété est défini par l’élément parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Value|Description|  
|-----------|-----------------|  
|*paramètre_stratégie*|Paramètre à appliquer à ce type de stratégie pour la propriété. Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  
 Si la stratégie d'une propriété n'est pas définie explicitement, elle hérite la stratégie runtime de son élément parent.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la réflexion pour instancier un objet `Book` et afficher les valeurs de ses propriétés. Le fichier default.rd.xml d'origine du projet se présente comme suit :  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Le fichier applique la valeur `All` à la stratégie `Activate` pour la classe `Book`, ce qui permet d'accéder aux constructeurs de classe par réflexion. La stratégie `Browse` pour la classe `Book` est héritée de son espace de noms parent. Cette option est définie sur `Required Public`, ce qui rend les métadonnées disponibles au moment de l'exécution.  
  
 Voici le code source de l'exemple. Le `outputBlock` variable représente un <xref:Windows.UI.Xaml.Controls.TextBlock> contrôle.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Cependant, la compilation et l’exécution de cet exemple lèvent une exception [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Bien que les métadonnées soient disponibles pour le type `Book`, nous n'avons pas pu rendre les implémentations des accesseurs Get de propriété disponibles dynamiquement. Nous pouvons corriger cette erreur de deux manières :  
  
- En définissant la stratégie `Dynamic` pour le type `Book` dans son élément [\<Type>](../../../docs/framework/net-native/type-element-net-native.md).  
  
- En ajoutant un élément [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) imbriqué pour chaque propriété dont nous souhaitons appeler le getter, comme le fait le fichier default.rd.xml suivant.  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
