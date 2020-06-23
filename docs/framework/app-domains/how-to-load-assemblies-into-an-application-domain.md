---
title: 'Procédure : charger des assemblys dans un domaine d’application'
description: Découvrez comment charger des assemblys dans un domaine d’application dans .NET. La méthode recommandée consiste à utiliser la méthode Load statique (ou Shared) dans System. Reflection. assembly.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c91c70625b79002e9297755dfdfac8aa6e283208
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104755"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Procédure : charger des assemblys dans un domaine d’application
Il existe plusieurs façons de charger un assembly dans un domaine d’application. La procédure recommandée consiste à utiliser la méthode `static` (`Shared` en Visual Basic) <xref:System.Reflection.Assembly.Load%2A> de la classe <xref:System.Reflection.Assembly?displayProperty=nameWithType>. Vous pouvez aussi adopter les approches suivantes :  
  
- La méthode <xref:System.Reflection.Assembly.LoadFrom%2A> de la classe <xref:System.Reflection.Assembly> charge un assembly en fonction de son emplacement de fichier. Le chargement des assemblys avec cette méthode utilise un contexte de chargement différent.  
  
- Les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> chargent un assembly dans le contexte de réflexion uniquement. Les assemblys chargés dans ce contexte peuvent être examinés mais pas exécutés, ce qui permet d’examiner des assemblys qui ciblent d’autres plateformes. Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
> Le contexte de réflexion uniquement est une nouveauté du .NET Framework version 2.0.  
  
- Les méthodes telles que <xref:System.AppDomain.CreateInstance%2A> et <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> de la classe <xref:System.AppDomain> peuvent charger des assemblys dans un domaine d’application.  
  
- La méthode <xref:System.Type.GetType%2A> de la classe <xref:System.Type> peut charger des assemblys.  
  
- La méthode <xref:System.AppDomain.Load%2A> de la classe <xref:System.AppDomain?displayProperty=nameWithType> peut charger des assemblys, mais est utilisée principalement pour l’interopérabilité COM. Vous ne devez pas l’utiliser pour charger des assemblys dans un domaine d’application autre que celui à partir duquel elle est appelée.  
  
> [!NOTE]
> À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime actuellement chargé. Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.  
  
 Vous pouvez spécifier la façon dont le code compilé juste-à-temps (JIT) des assemblys chargés est partagé entre les domaines d’application. Pour plus d’informations, consultez [domaines d’application et assemblys](application-domains.md#application-domains-and-assemblies).  
  
## <a name="example"></a>Exemple  
 Le code suivant charge un assembly nommé « example.exe » ou « example.dll » dans le domaine d’application actuel, obtient un type nommé `Example` à partir de l’assembly, obtient une méthode sans paramètre nommée `MethodA` pour ce type, et exécute la méthode. Pour obtenir une description complète de l’obtention d’informations à partir d’un assembly chargé, consultez [Chargement et utilisation dynamiques des types](../reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [Programmation avec des domaines d’application](application-domains.md#programming-with-application-domains)
- [Réflexion](../reflection-and-codedom/reflection.md)
- [Utilisation des domaines d'application](use.md)
- [Procédure : charger des assemblys dans le contexte de réflexion uniquement](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [Domaines d’application et assemblys](application-domains.md#application-domains-and-assemblies)
