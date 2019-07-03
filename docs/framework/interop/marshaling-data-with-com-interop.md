---
title: marshaler des données avec COM Interop
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16f94e8b85a1bedb8b7791c2b7fcaf6d154ba1b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833521"
---
# <a name="marshaling-data-with-com-interop"></a>marshaler des données avec COM Interop
COM Interop prend en charge l'utilisation des objets COM à partir de code managé, ainsi que l'exposition des objets managés à COM. La prise en charge du marshaling des données vers et depuis COM est complète et fournit quasiment toujours le comportement de marshaling approprié.  
  
 Le Kit de développement logiciel (SDK) Windows inclut les outils COM interop suivants :  
  
- [Importateur de bibliothèques de types (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), qui convertit une bibliothèque de types COM en un assembly d’interopérabilité. À partir de cet assembly, le service de marshaling d'interopérabilité génère des wrappers qui effectuent le marshaling des données entre la mémoire managée et non managée.  
  
- [Exportateur de bibliothèques de types (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), qui produit une bibliothèque de types COM à partir d’un assembly et génère un wrapper qui effectue le marshaling lors des appels de méthode.  
  
 Les sections suivantes fournissent des liens vers des rubriques qui décrivent les processus de personnalisation des wrappers d’interopérabilité quand vous pouvez (ou devez) fournir au marshaleur des informations supplémentaires concernant les types.  
  
## <a name="in-this-section"></a>Dans cette section  
[Guide pratique pour créer manuellement des wrappers](how-to-create-wrappers-manually.md)   
Décrit comment créer manuellement un wrapper COM dans du code source managé. 
 
 [Guide pratique pour migrer du code DCOM managé vers WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Décrit comment migrer du code DCOM managé vers WCF pour obtenir la solution la plus sécurisée.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de données COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Fournit les types de données managés et non managés correspondants.  
  
 [Personnalisation des wrappers CCW (COM Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Décrit comment marshaler explicitement des types de données à l’aide de l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> au moment du design.  
  
 [Personnalisation des wrappers RCW (Runtime Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Décrit comment ajuster le comportement de marshaling des types dans un assembly d'interopérabilité et comment définir des types COM manuellement.  
  
 [Interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.  
  
 [Récapitulatif de la conversion d’un assembly en bibliothèque de types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Décrit le processus d'exportation et de conversion d'un assembly en une bibliothèque de types.  
  
 [Récapitulatif de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Décrit le processus d'importation et de conversion d'une bibliothèque de types en un assembly.  
  
 [Interopérabilité à l’aide de types génériques](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Décrit les actions prises en charge lors de l'utilisation de types génériques pour l'interopérabilité COM.
