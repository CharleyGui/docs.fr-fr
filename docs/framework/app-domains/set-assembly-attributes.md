---
title: Définition des attributs d'assembly
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ea8c1f01c62075fc4399cada282128e07422d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607541"
---
# <a name="setting-assembly-attributes"></a>Définition des attributs d'assembly
Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly. Les attributs sont répartis selon les ensembles d’informations suivants :  
  
- Attributs d’identité de l’assembly  
  
- Attributs d’informations  
  
- Attributs de manifeste de l’assembly  
  
- Attributs de nom fort  
  
## <a name="assembly-identity-attributes"></a>Attributs d’identité de l’assembly  
 Trois attributs avec un nom fort (le cas échéant), déterminent l’identité d’un assembly : nom, version et culture. Ces attributs constituent le nom complet de l’assembly et sont requis lorsque vous référencez l’assembly dans le code. Vous pouvez utiliser les attributs pour définir la version et la culture d’un assembly. Le compilateur ou l’utilitaire [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) définit la valeur du nom lors de la création de l’assembly, en fonction du fichier contenant le manifeste de l’assembly.  
  
 Le tableau suivant décrit les attributs de version et de culture.  
  
|Attribut d’identité de l’assembly|Description|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Champ énuméré désignant la culture que l’assembly prend en charge. Un assembly peut également spécifier une indépendance de culture, indiquant qu’il contient les ressources pour la culture par défaut. **Remarque :**  le runtime gère tout assembly dont l’attribut de culture n’est pas défini sur Null comme un assembly satellite. Ces assemblys sont soumis aux règles de liaison d’assembly satellite. Pour plus d’informations, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Valeur qui définit les attributs d’assembly, par exemple l’exécution côte à côte de l’assembly.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Valeur numérique au format *version principale*.*version secondaire*.*build*.*révision* (p. ex. 2.4.0.0). Le common language runtime utilise cette valeur pour effectuer les opérations de liaison dans les assemblys avec nom fort. **Remarque :**  Si l’attribut <xref:System.Reflection.AssemblyInformationalVersionAttribute> n’est pas appliqué à un assembly, le numéro de version spécifié par l’attribut <xref:System.Reflection.AssemblyVersionAttribute> est utilisé par les propriétés <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.|  
  
 L’exemple de code suivant montre comment appliquer les attributs de version et de culture à un assembly.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Attributs d’informations  
 Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly. Le tableau suivant décrit les attributs d’informations que vous pouvez appliquer à l’assembly.  
  
|Attributs d’informations|Description|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Valeur de chaîne qui spécifie un nom de société.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Valeur de chaîne qui spécifie les informations de copyright.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Valeur de chaîne qui spécifie le numéro de version du fichier Win32. Par défaut, il s’agit normalement de la version de l’assembly.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Valeur de chaîne qui spécifie les informations de version qui ne sont pas utilisées par le common language runtime, comme un numéro de version du produit complet. **Remarque :**  si cet attribut est appliqué à un assembly, la chaîne qu’il spécifie peut être obtenue à l’exécution avec la propriété <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>. Cette chaîne est également utilisée dans le chemin d’accès et la clé de Registre fournis par les propriétés <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Valeur de chaîne qui spécifie les informations de produit.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Valeur de chaîne qui spécifie les informations de marque.|  
  
 Ces attributs peuvent apparaître sur la page Propriétés Windows de l’assembly, ou ils peuvent être remplacés à l’aide de l’option **/win32res** du compilateur pour spécifier votre propre fichier de ressources Win32.  
  
## <a name="assembly-manifest-attributes"></a>Attributs de manifeste de l’assembly  
 Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly, y compris le titre, la description, l’alias par défaut et la configuration. Le tableau suivant décrit les attributs de manifeste de l’assembly.  
  
|Attribut de manifeste de l’assembly|Description|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Valeur de chaîne désignant la configuration de l’assembly, comme Retail ou Debug. Le runtime n’utilise pas cette valeur.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Valeur de chaîne qui spécifie un alias par défaut à utiliser en référençant les assemblys. Cette valeur fournit un nom convivial lorsque le nom de l’assembly ne l’est pas (comme une valeur GUID). Cette valeur peut également être utilisée comme une forme abrégée du nom complet de l’assembly.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Valeur de chaîne désignant une brève description qui résume la nature et l’objectif de l’assembly.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Valeur de chaîne qui spécifie un nom convivial pour l’assembly. Par exemple, un assembly appelé comdlg peut être nommé Contrôle boîte de dialogue commune Microsoft.|  
  
## <a name="strong-name-attributes"></a>Attributs de nom fort  
 Vous pouvez utiliser les attributs de nom fort pour définir un nom fort pour l’assembly. Le tableau suivant décrit les attributs de nom fort.  
  
|Attributs de nom fort|Description|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Valeur booléenne qui indique que la signature différée est utilisée.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Valeur de chaîne qui indique le nom du fichier contenant soit la clé publique (si la signature différée est utilisée), soit les clés publiques et privées transmises en tant que paramètres au constructeur de cet attribut. Notez que le nom de fichier est relatif au chemin d’accès du fichier de sortie (.exe ou .dll), et non au chemin d’accès du fichier source.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Indique le conteneur de clé qui possède la paire de clés transmise en tant que paramètre au constructeur de cet attribut.|  
  
 L’exemple de code suivant montre les attributs à appliquer lors de l’utilisation de la signature différée pour créer un assembly avec nom fort avec un fichier de clé publique appelé `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)
- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
