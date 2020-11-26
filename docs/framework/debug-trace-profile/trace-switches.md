---
title: Commutateurs de traçage
description: Explorez les commutateurs de trace, qui vous permettent d’activer, de désactiver et de filtrer la sortie de traçage. .NET fournit les classes BooleanSwitch, TraceSwitch et SourceSwitch.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
ms.openlocfilehash: dfbff0a78b3c6c1318224ccc9608c1b816f9d5f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238052"
---
# <a name="trace-switches"></a>Commutateurs de traçage

Les commutateurs de trace vous permettent d'activer ou de désactiver la sortie de traçage, et de la filtrer. Ces commutateurs sont des objets présents dans votre code, mais ils peuvent être configurés en dehors du code via le fichier .config. Trois types de commutateurs de trace sont disponibles dans .NET Framework : la classe <xref:System.Diagnostics.BooleanSwitch> , la classe <xref:System.Diagnostics.TraceSwitch> et la classe <xref:System.Diagnostics.SourceSwitch> . La classe <xref:System.Diagnostics.BooleanSwitch> agit comme un bouton bascule qui active ou désactive diverses instructions de trace. Les classes <xref:System.Diagnostics.TraceSwitch> et <xref:System.Diagnostics.SourceSwitch> vous permettent d'activer un commutateur de trace pour un niveau de traçage spécifique. Les messages <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.TraceSource> spécifiés pour ce niveau et tous les niveaux inférieurs seront alors affichés. Si vous désactivez le commutateur, les messages de trace ne seront pas affichés. Toutes ces classes dérivent de la classe abstraite (**MustInherit**) **Switch**, comme tous les commutateurs créés par l'utilisateur.  
  
 Les commutateurs de trace sont parfois utiles pour filtrer des informations. Supposons que vous vouliez afficher tous les messages de trace dans un module d'accès aux données, mais afficher uniquement les messages d'erreur dans les autres parties de l'application. Dans ce cas, vous pouvez utiliser un commutateur de trace pour le module d'accès aux données et un deuxième commutateur pour les autres parties de l'application. Si vous utilisez le fichier .config pour configurer les commutateurs avec les paramètres appropriés, vous pouvez déterminer les types de messages de trace que vous recevez. Pour plus d’informations, consultez [Guide pratique pour créer, initialiser et configurer des commutateurs de suivi](how-to-create-initialize-and-configure-trace-switches.md).  
  
 En règle générale, une application déployée s'exécute sans que les commutateurs ne soient activés. Cela évite aux utilisateurs de voir s'afficher de nombreux messages inutiles à l'écran ou que ces messages soient enregistrés dans un fichier journal durant l'exécution de l'application. Si un problème survient au cours de l'exécution de l'application, vous pouvez arrêter l'application, activer les commutateurs et redémarrer l'application pour afficher les messages de trace.  
  
 Pour utiliser un commutateur, vous devez tout d'abord créer un objet commutateur à partir d'une classe **BooleanSwitch** , d'une classe **TraceSwitch** ou d'une classe de commutateur définie par le développeur. Pour plus d’informations sur la création de commutateurs définis par le développeur, consultez la classe <xref:System.Diagnostics.Switch> dans la référence .NET Framework. Définissez ensuite une valeur de configuration qui spécifie à quel moment l'objet commutateur doit être utilisé. Enfin, testez le paramètre de l'objet commutateur dans plusieurs méthodes de traçage **Trace** (ou **Debug**).  
  
## <a name="trace-levels"></a>Niveaux de trace  

 Quand vous utilisez **TraceSwitch**, d'autres aspects sont à prendre en compte. Un objet **TraceSwitch** possède quatre propriétés qui retournent des valeurs de type **Boolean** indiquant si au moins un niveau de trace est défini pour le commutateur :  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Les niveaux vous permettent de limiter la quantité d'informations de traçage reçues à celles qui sont nécessaires pour résoudre un problème. Vous spécifiez le niveau de détail souhaité dans la sortie de traçage en définissant et en configurant les commutateurs de trace avec le niveau de trace approprié. Vous pouvez choisir de recevoir les messages d'erreur, les messages d'avertissement, les messages d'information, les messages de trace détaillés ou, au contraire, de ne recevoir aucun message.  
  
 C'est vous qui déterminez le type de message à associer à chaque niveau. Généralement, le contenu des messages de trace dépend de ce que vous associez à chaque niveau, mais vous déterminez les différences entre les niveaux. Vous pouvez, par exemple, choisir d'afficher une description détaillée d'un problème au niveau 3 (**Info**), mais uniquement un numéro de référence d'erreur au niveau 1 (**Error**). Choisissez le schéma le plus approprié pour votre application.  
  
 Ces propriétés correspondent aux valeurs 1 à 4 de l'énumération **TraceLevel** . Le tableau suivant répertorie les niveaux de l'énumération **TraceLevel** et leurs valeurs.  
  
|Valeur énumérée|Valeur entière|Type de message affiché (ou écrit vers une cible de sortie spécifiée)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Désactivé|0|None|  
|Error|1|Uniquement les messages d'erreur|  
|Avertissement|2|Messages d'avertissement et messages d'erreur|  
|Info|3|Messages d'information, messages d'avertissement et messages d'erreur|  
|Commentaires|4|Messages détaillés, messages d'information, messages d'avertissement et messages d'erreur|  
  
 Les propriétés **TraceSwitch** indiquent le niveau de trace maximal pour le commutateur. Autrement dit, les informations de traçage sont écrites pour le niveau spécifié et tous les niveaux inférieurs. Par exemple, si **TraceInfo** a la valeur **true**, **TraceError** et **TraceWarning** ont également la valeur **true** , mais **TraceVerbose** peut très bien avoir la valeur **false**.  
  
 Ces propriétés sont en lecture seule. L'objet **TraceSwitch** les définit automatiquement quand la propriété **TraceLevel** est définie. Par exemple :  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a>Commutateurs définis par le développeur  

 En plus des commutateurs **BooleanSwitch** et **TraceSwitch**, vous pouvez définir vos propres commutateurs en les dérivant de la classe **Switch** et en remplaçant les méthodes de la classe de base par des méthodes personnalisées. Pour plus d’informations sur la création de commutateurs définis par le développeur, consultez la classe <xref:System.Diagnostics.Switch> dans la référence .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [Écouteurs de suivi](trace-listeners.md)
- [Procédure : Ajouter des instructions de trace dans le code d’une application](how-to-add-trace-statements-to-application-code.md)
- [Traçage et instrumentation d’applications](tracing-and-instrumenting-applications.md)
