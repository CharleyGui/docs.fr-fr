---
title: 'Procédure : générer des assemblys d’interopérabilité à partir de bibliothèques de types'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcdff732afce90f725f4730f0054296e389ada1b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051786"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Procédure : générer des assemblys d’interopérabilité à partir de bibliothèques de types
L’outil en ligne de commande [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md) permet de convertir les coclasses et les interfaces figurant dans une bibliothèque de types COM en métadonnées. Cet outil crée automatiquement un assembly d’interopérabilité et un espace de noms pour les informations sur les types. Une fois les métadonnées d’une classe disponibles, les clients managés peuvent créer des instances du type COM et appeler ses méthodes, comme s’il s’agissait d’une instance .NET. Tlbimp.exe convertit en une seule opération l’intégralité d’une bibliothèque de types en métadonnées et ne peut pas générer d’informations sur les types pour un sous-ensemble de types définis dans une bibliothèque de types.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Pour générer un assembly d’interopérabilité à partir d’une bibliothèque de types  
  
1. Utilisez la commande suivante :  
  
     **tlbimp** \<*fichier-bibliothèque-types*>  
  
     L’ajout du commutateur **/out:** produit un assembly d’interopérabilité avec un nom modifié (LOANLib.dll, par exemple). La modification du nom de l’assembly d’interopérabilité peut aider à le distinguer de la DLL COM d’origine et évite les problèmes qui peuvent survenir quand des noms sont dupliqués.  
  
## <a name="example"></a>Exemple  
 La commande suivante produit l’assembly Loanlib.dll dans l’espace de noms `Loanlib`.  
  
```  
tlbimp Loanlib.tlb  
```  
  
 La commande suivante produit un assembly d’interopérabilité avec un nom modifié (LOANLib.dll).  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Voir aussi

- [Importation d'une bibliothèque de types sous la forme d'un assembly](importing-a-type-library-as-an-assembly.md)
- [Exposition de composants COM au .NET Framework](exposing-com-components.md)
