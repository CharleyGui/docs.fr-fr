---
title: 'Procédure : référencer des types .NET à partir de COM'
description: Référencez des types .NET à partir de COM. Les clients VB peuvent afficher un objet .NET dans l’Explorateur d’objets, mais les clients C++ doivent faire référence à un fichier TLB avec la \# directive import.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: fad0a8163bd3d023911fd8554a77f740ac010ee6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547243"
---
# <a name="how-to-reference-net-types-from-com"></a>Procédure : référencer des types .NET à partir de COM
Du point de vue du code client et serveur, les différences entre COM et le .NET Framework sont largement invisibles. Les clients Microsoft Visual Basic peuvent afficher un objet .NET dans l’Explorateur d’objets, qui expose la syntaxe et les méthodes de l’objet, les propriétés et les champs exactement comme s’il s’agissait de tout autre objet COM.  
  
 Le processus d’importation d’une bibliothèque de types est légèrement plus compliqué pour les clients C++, même si vous utilisez les mêmes outils pour exporter des métadonnées vers une bibliothèque de types COM. Pour référencer des membres d’objet .NET à partir d’un client C++ non managé, référencez le fichier TLB (produit à l’aide de Tlbexp.exe) avec la directive **#import**. Lors du référencement d’une bibliothèque de types à partir de C++, vous devez soit spécifier l’option **raw_interfaces_only**, soit importer les définitions dans la bibliothèque de classes de base Mscorlib.tlb.  
  
### <a name="to-import-a-library"></a>Pour importer une bibliothèque  
  
- Spécifiez l’option **raw_interfaces_only** dans la directive **#import**. Exemple :  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     - ou -  
  
- Ajoutez une directive #import pour Mscorlib.tlb. Par exemple :  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Exposition de composants .NET Framework à COM](exposing-dotnet-components-to-com.md)
- [Inscription d'assemblys dans COM](registering-assemblies-with-com.md)
- [Appeler un objet .NET](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Déployer une application pour accéder à COM](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
