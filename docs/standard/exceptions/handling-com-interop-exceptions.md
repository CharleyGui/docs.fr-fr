---
title: Gestion des exceptions COM Interop
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 058fb6446f69c2e10cb136ce5b5ad73b14d82647
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828138"
---
# <a name="handling-com-interop-exceptions"></a>Gestion des exceptions COM Interop
Le code managé et le code non managé peuvent collaborer pour gérer les exceptions. Si une méthode lève une exception dans du code managé, le common language runtime peut passer HRESULT à un objet COM. Si une méthode échoue dans du code non managé en retournant un échec HRESULT, le runtime lève une exception qui peut être interceptée par du code managé.  
  
 Le runtime mappe automatiquement la valeur HRESULT de COM Interop à des exceptions plus spécifiques. Par exemple, E_ACCESSDENIED devient <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY devient <xref:System.OutOfMemoryException>, etc.  
  
 Si la valeur HRESULT est un résultat personnalisé ou si elle est inconnue du runtime, le runtime passe une exception générique <xref:System.Runtime.InteropServices.COMException> au client. La propriété **ErrorCode** de la **COMException** contient la valeur HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Utilisation d'IErrorInfo  
 Quand une erreur est passée de COM à du code managé, le runtime renseigne l'objet exception avec les informations de l'erreur. Les objets COM qui prennent en charge IErrorInfo et qui retournent des valeurs HRESULT fournissent ces informations aux exceptions du code managé. Par exemple, le runtime mappe la description de l'erreur COM à la propriété <xref:System.Exception.Message%2A> de l'exception. Si la valeur HRESULT ne fournit pas d'informations d'erreur supplémentaires, le runtime renseigne un grand nombre de propriétés de l'exception avec des valeurs par défaut.  
  
 Si une méthode échoue dans du code non managé, une exception peut être passée à un segment de code managé. La rubrique [Valeurs HRESULT et exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contient un tableau montrant comment les valeurs HRESULT sont mappées aux objets exception du runtime.  

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
