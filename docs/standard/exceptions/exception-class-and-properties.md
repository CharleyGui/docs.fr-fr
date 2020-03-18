---
title: Classe et propriétés d'exception
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
ms.openlocfilehash: df05150a5bdd5d24766be252f5cec9a436720d8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708943"
---
# <a name="exception-class-and-properties"></a>Classe et propriétés d’exception

La classe <xref:System.Exception> est la classe de base dont héritent les exceptions. Par exemple, la hiérarchie de classes <xref:System.InvalidCastException> se présente comme suit :

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

La classe <xref:System.Exception> a les propriétés suivantes qui vous permettront de mieux comprendre une exception.

| Nom de la propriété | Description |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> qui contient des données arbitraires dans des paires clé-valeur. |
| <xref:System.Exception.HelpLink> | Peut contenir une URL (ou URN) vers un fichier d’aide qui fournit des informations détaillées sur la cause d’une exception. |
| <xref:System.Exception.InnerException> | Cette propriété peut être utilisée pour créer et conserver une série d’exceptions pendant la gestion des exceptions. Vous pouvez l’utiliser pour créer une exception qui contient des exceptions interceptées précédemment. L’exception d’origine peut être capturée par la deuxième exception dans la propriété <xref:System.Exception.InnerException>, ce qui permet au code qui gère la deuxième exception d’examiner les informations supplémentaires. Par exemple, supposons que vous disposez d’une méthode qui reçoit un argument avec une mise en forme incorrecte.  Le code essaie de lire l’argument, mais une exception est levée. La méthode intercepte l’exception et lève une exception <xref:System.FormatException>. Pour améliorer la capacité de l’appelant à déterminer la raison pour laquelle une exception est levée, il est parfois souhaitable qu’une méthode intercepte une exception levée par une routine d’assistance, puis qu’elle lève une exception plus évocatrice de l’erreur qui s’est produite. Une exception plus significative peut être créée, dans laquelle la référence à l’exception interne peut être définie sur l’exception d’origine. Cette exception plus significative peut ensuite être levée pour l’appelant. Notez que cette fonctionnalité vous permet de créer une série d’exceptions liées qui se termine avec l’exception initialement levée. |
| <xref:System.Exception.Message> | Fournit les détails de la cause d’une exception.
| <xref:System.Exception.Source> | Obtient ou définit le nom de l'application ou de l'objet qui est à l'origine de l'erreur. |
| <xref:System.Exception.StackTrace>| Contient une trace de pile qui peut être utilisée pour déterminer où une erreur s’est produite. La trace de la pile comprend le nom du fichier source et le numéro de ligne du programme si les informations de débogage sont disponibles. |

La plupart des classes qui héritent de <xref:System.Exception> n’implémentent pas de membres supplémentaires ni ne fournissent de fonctionnalités supplémentaires, elles héritent simplement de <xref:System.Exception>. Par conséquent, vous pouvez trouver les informations les plus importantes d’une exception dans la hiérarchie des classes d’exception, le nom de l’exception et les informations contenues dans l’exception.

Nous vous recommandons de lever et d’intercepter uniquement des objets qui dérivent de <xref:System.Exception>, mais vous pouvez lever comme exception n’importe quel objet qui dérive de la classe <xref:System.Object>. Notez que tous les langages ne prennent pas forcément en charge la levée et l’interception d’objets qui ne dérivent pas de <xref:System.Exception>.
  
## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
