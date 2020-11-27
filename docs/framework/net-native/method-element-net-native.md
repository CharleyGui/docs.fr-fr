---
title: <Method> , Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 1d57457c90e44c70caa301eccc02c5831d283cea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287902"
---
# <a name="method-element-net-native"></a>\<Method> , Élément (.NET Native)

Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom de la méthode.|  
|`Signature`|Général|Attribut facultatif. Spécifie la signature de la méthode. Si plusieurs paramètres sont présents, ils sont séparés par des virgules. Par exemple, l'élément `<Method>` suivant définit la stratégie pour la méthode <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Si l'attribut est absent, la directive runtime s'applique à toutes les surcharges de la méthode.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur une méthode ou l'énumération de celle-ci, mais ne permet pas d'effectuer un appel dynamique au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à un constructeur ou à une méthode au moment de l'exécution pour activer la programmation dynamique. Cette stratégie garantit que le membre peut être appelé dynamiquement au moment de l'exécution.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*method_name*|Nom de la méthode. Le type de la méthode est défini par l' [\<Type>](type-element-net-native.md) élément parent ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .|  
  
## <a name="signature-attribute"></a>Attribut de signature  
  
|Valeur|Description|  
|-----------|-----------------|  
|*signature_méthode*|Types de paramètre qui constituent la signature de la méthode. Si plusieurs paramètres sont présents, ils sont séparés par des virgules. Par exemple : `"System.String,System.Int32,System.Int32)"`. Les noms de type de paramètre doivent être qualifiés complets.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie. Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|Applique la stratégie au type de l'argument passé à une méthode.|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|Applique la stratégie au type de paramètre d'un type ou d'une méthode générique.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Applique la stratégie à un type, si cette stratégie a été appliquée à la méthode représentée par l'élément `<Method>` conteneur.|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|Applique la stratégie au type représenté par un argument <xref:System.Type> passé à une méthode.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  

 Un élément `<Method>` d'une méthode générique applique sa stratégie à toutes les instanciations qui n'ont pas leur propre stratégie.  
  
 Vous pouvez utiliser l'attribut `Signature` pour spécifier la stratégie d'une surcharge de méthode particulière. Sinon, si l'attribut `Signature` est absent, la directive runtime s'applique à toutes les surcharges de la méthode.  
  
 Vous ne pouvez pas définir la stratégie de réflexion runtime d'un constructeur à l'aide de l'élément `<Method>`. Utilisez plutôt l' `Activate` attribut de l'  [\<Assembly>](assembly-element-net-native.md) élément, [\<Namespace>](namespace-element-net-native.md) , [\<Type>](type-element-net-native.md) ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
## <a name="example"></a> Exemple  

 La méthode `Stringify` dans l'exemple suivant est une méthode de mise en forme à usage général qui utilise la réflexion pour convertir un objet sous forme de chaîne. En plus d'appeler la méthode `ToString` par défaut de l'objet, la méthode peut produire une chaîne de résultat mise en forme en passant à la méthode `ToString` d'un objet une chaîne de format et/ou une implémentation <xref:System.IFormatProvider>. Elle peut également appeler l'une des surcharges <xref:System.Convert.ToString%2A?displayProperty=nameWithType> qui convertit un nombre au format binaire, hexadécimale ou octale.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 La méthode `Stringify` peut être appelée par du code comme suit :  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Toutefois, quand il est compilé avec .NET Native, l’exemple peut lever de nombreuses exceptions au moment de l’exécution, notamment les exceptions <xref:System.NullReferenceException> et [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md). En effet, la méthode `Stringify` est principalement destinée à prendre en charge la mise en forme dynamique des types primitifs dans la bibliothèque de classes .NET Framework. Cependant, leurs métadonnées ne sont pas rendues disponibles par le fichier de directives par défaut. Toutefois, même quand leurs métadonnées sont rendues disponibles, l’exemple lève des exceptions [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md), car les implémentations `ToString` appropriées n’ont pas été incluses dans le code natif.  
  
 Ces exceptions peuvent être éliminées en utilisant l' [\<Type>](type-element-net-native.md) élément pour définir les types dont les métadonnées doivent être présentes et en ajoutant des `<Method>` éléments pour garantir que l’implémentation de surcharges de méthode qui peuvent être appelées de façon dynamique est également présente. Voici le fichier default.rd.xml qui élimine ces exceptions et qui permet à l'exemple de s'exécuter sans erreur.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
- [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md)
- [\<MethodInstantiation> Appartient](methodinstantiation-element-net-native.md)
