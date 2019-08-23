---
title: Dépannage des problèmes liés à l'interopérabilité (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: c04cd0928eb83aabcd1f0f4b1b43f8ae6d356d20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969323"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Dépannage des problèmes liés à l'interopérabilité (Visual Basic)
Lorsque vous interagissez entre COM et le code managé du .NET Framework, vous pouvez rencontrer un ou plusieurs des problèmes courants suivants.  
  
## <a name="vbconinteroperabilitymarshalinganchor1"></a>Marshaling d’interopérabilité  
 Parfois, vous devrez peut-être utiliser des types de données qui ne font pas partie du .NET Framework. Les assemblys d’interopérabilité gèrent la majeure partie du travail pour les objets COM, mais vous devrez peut-être contrôler les types de données utilisés lorsque des objets managés sont exposés à COM. Par exemple, les structures dans les bibliothèques de classes `BStr` doivent spécifier le type non managé sur les chaînes envoyées aux objets COM créés par Visual Basic 6,0 et versions antérieures. Dans ce cas, vous pouvez utiliser l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut pour que les types managés soient exposés en tant que types non managés.  
  
## <a name="vbconinteroperabilitymarshalinganchor2"></a>Exportation de chaînes de longueur fixe vers du code non managé  
 Dans Visual Basic 6,0 et versions antérieures, les chaînes sont exportées vers les objets COM sous forme de séquences d’octets sans caractère de fin null. Pour la compatibilité avec d’autres langages, Visual Basic .NET comprend un caractère d’arrêt lors de l’exportation de chaînes. La meilleure façon de résoudre cette incompatibilité consiste à exporter des chaînes qui n’ont pas de caractère de fin `Byte` en `Char`tant que tableaux de ou.  
  
## <a name="vbconinteroperabilitymarshalinganchor3"></a>Exportation des hiérarchies d’héritage  
 Les hiérarchies de classes managées sont aplaties quand elles sont exposées en tant qu’objets COM. Par exemple, si vous définissez une classe de base avec un membre, puis que vous héritez de la classe de base dans une classe dérivée qui est exposée en tant qu’objet COM, les clients qui utilisent la classe dérivée dans l’objet COM ne pourront pas utiliser les membres hérités. Les membres de la classe de base sont accessibles uniquement à partir d’objets COM en tant qu’instances d’une classe de base, puis uniquement si la classe de base est également créée en tant qu’objet COM.  
  
## <a name="overloaded-methods"></a>Méthodes surchargées  
 Bien que vous puissiez créer des méthodes surchargées avec Visual Basic, elles ne sont pas prises en charge par COM. Lorsqu’une classe qui contient des méthodes surchargées est exposée en tant qu’objet COM, de nouveaux noms de méthode sont générés pour les méthodes surchargées.  
  
 Par exemple, considérez une classe qui a deux surcharges de `Synch` la méthode. Lorsque la classe est exposée en tant qu’objet com, les nouveaux noms de méthode `Synch` générés peuvent être et `Synch_2`.  
  
 Le changement de nom peut entraîner deux problèmes pour les consommateurs de l’objet COM.  
  
1. Les clients peuvent ne pas s’attendre à recevoir les noms de méthode générés.  
  
2. Les noms de méthode générés dans la classe exposée comme un objet COM peuvent changer quand de nouvelles surcharges sont ajoutées à la classe ou à sa classe de base. Cela peut entraîner des problèmes de contrôle de version.  
  
 Pour résoudre les deux problèmes, attribuez un nom unique à chaque méthode, au lieu d’utiliser la surcharge, lorsque vous développez des objets qui seront exposés en tant qu’objets COM.  
  
## <a name="vbconinteroperabilitymarshalinganchor4"></a>Utilisation d’objets COM par le biais d’assemblys d’interopérabilité  
 Vous utilisez les assemblys d’interopérabilité presque comme s’il s’agissait de remplacements de code managé pour les objets COM qu’ils représentent. Toutefois, étant donné qu’il s’agit de wrappers et non d’objets COM réels, il existe des différences entre l’utilisation des assemblys d’interopérabilité et des assemblys standard. Ces zones de différence incluent l’exposition des classes, et les types de données pour les paramètres et les valeurs de retour.  
  
## <a name="vbconinteroperabilitymarshalinganchor5"></a>Classes exposées comme des interfaces et des classes  
 Contrairement aux classes des assemblys standard, les classes COM sont exposées dans les assemblys d’interopérabilité à la fois comme une interface et une classe qui représente la classe COM. Le nom de l’interface est identique à celui de la classe COM. Le nom de la classe Interop est le même que celui de la classe COM d’origine, mais avec le mot «Class» ajouté. Par exemple, supposons que vous ayez un projet avec une référence à un assembly d’interopérabilité pour un objet COM. Si la classe com est nommée `MyComClass`, IntelliSense et l’Explorateur d’objets affichent une `MyComClass` interface nommée et une `MyComClassClass`classe nommée.  
  
## <a name="vbconinteroperabilitymarshalinganchor6"></a>Création d’instances d’une classe .NET Framework  
 En général, vous créez une instance d’une classe .NET Framework à `New` l’aide de l’instruction avec un nom de classe. Avoir une classe com représentée par un assembly d’interopérabilité est le seul cas dans lequel vous `New` pouvez utiliser l’instruction avec une interface. À moins que vous n’utilisiez la classe `Inherits` com avec une instruction, vous pouvez utiliser l’interface comme vous le feriez pour une classe. Le code suivant montre comment créer un `Command` objet dans un projet qui a une référence à l’objet com de la bibliothèque Microsoft ActiveX Data Objects 2,8:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Toutefois, si vous utilisez la classe COM comme base pour une classe dérivée, vous devez utiliser la classe Interop qui représente la classe COM, comme dans le code suivant:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Les assemblys d’interopérabilité implémentent implicitement des interfaces qui représentent des classes COM. Vous ne devez pas essayer d’utiliser `Implements` l’instruction pour implémenter ces interfaces, sinon une erreur se produit.  
  
## <a name="vbconinteroperabilitymarshalinganchor7"></a>Types de données pour les paramètres et les valeurs de retour  
 Contrairement aux membres des assemblys standard, les membres d’assembly d’interopérabilité peuvent avoir des types de données qui diffèrent de ceux utilisés dans la déclaration d’objet d’origine. Bien que les assemblys d’interopérabilité convertissent implicitement les types COM en types de common language runtime compatibles, vous devez prêter attention aux types de données utilisés par les deux côtés pour éviter les erreurs d’exécution. Par exemple, dans les objets COM créés dans Visual Basic 6,0 et versions antérieures, les valeurs `Integer` de type adoptent le .NET Framework `Short`type équivalent,. Il est recommandé d’utiliser l’Explorateur d’objets pour examiner les caractéristiques des membres importés avant de les utiliser.  
  
## <a name="vbconinteroperabilitymarshalinganchor8"></a>Méthodes COM au niveau du module  
 La plupart des objets com sont utilisés en créant une instance d’une classe com `New` à l’aide du mot clé, puis en appelant les méthodes de l’objet. Une exception à cette règle concerne les objets COM qui `AppObj` contiennent `GlobalMultiUse` des classes com ou. Ces classes ressemblent aux méthodes de niveau module dans Visual Basic les classes .NET. Visual Basic 6,0 et les versions antérieures créent implicitement des instances de ces objets pour vous la première fois que vous appelez l’une de leurs méthodes. Par exemple, dans Visual Basic 6,0, vous pouvez ajouter une référence à la bibliothèque d’objets Microsoft DAO 3,6 et `DBEngine` appeler la méthode sans créer au préalable une instance:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET requiert que vous soyez toujours en mesure de créer des instances d’objets COM avant de pouvoir utiliser leurs méthodes. Pour utiliser ces méthodes dans Visual Basic, déclarez une variable de la classe souhaitée et utilisez le mot clé New pour assigner l’objet à la variable objet. Le `Shared` mot clé peut être utilisé lorsque vous voulez vous assurer qu’une seule instance de la classe est créée.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="vbconinteroperabilitymarshalinganchor9"></a>Erreurs non gérées dans les gestionnaires d’événements  
 Un problème d’interopérabilité courant implique des erreurs dans les gestionnaires d’événements qui gèrent les événements déclenchés par les objets COM. Ces erreurs sont ignorées, sauf si vous recherchez spécifiquement `On Error` des `Try...Catch...Finally` erreurs à l’aide d’instructions ou. Par exemple, l’exemple suivant provient d’un projet .NET Visual Basic qui a une référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2,8.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 Cet exemple génère une erreur comme prévu. Toutefois, si vous essayez le même exemple sans le `Try...Catch...Finally` bloc, l’erreur est ignorée comme si vous utilisiez l' `OnError Resume Next` instruction. Sans la gestion des erreurs, la division par zéro échoue en silence. Étant donné que ces erreurs ne déclenchent jamais des erreurs d’exception non gérées, il est important d’utiliser une certaine forme de gestion des exceptions dans les gestionnaires d’événements qui gèrent des événements à partir d’objets COM.  
  
### <a name="understanding-com-interop-errors"></a>Compréhension des erreurs de COM Interop  
 Sans la gestion des erreurs, les appels Interop génèrent souvent des erreurs qui fournissent peu d’informations. Dans la mesure du possible, utilisez la gestion structurée des erreurs pour fournir plus d’informations sur les problèmes lorsqu’ils se produisent. Cela peut s’avérer particulièrement utile lorsque vous déboguez des applications. Par exemple :  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Vous pouvez trouver des informations telles que la description de l’erreur, HRESULT et la source des erreurs COM en examinant le contenu de l’objet exception.  
  
## <a name="vbconinteroperabilitymarshalinganchor10"></a>Problèmes liés aux contrôles ActiveX  
 La plupart des contrôles ActiveX qui fonctionnent avec Visual Basic 6,0 fonctionnent avec Visual Basic .NET sans aucun problème. Les principales exceptions sont les contrôles conteneurs, ou les contrôles qui contiennent visuellement d’autres contrôles. Voici quelques exemples de contrôles plus anciens qui ne fonctionnent pas correctement avec Visual Studio:  
  
- Contrôle Frame Microsoft Forms 2,0  
  
- Contrôle up-down, également appelé contrôle spin  
  
- Contrôle onglet Sheridan  
  
 Il n’existe que quelques solutions de contournement pour les problèmes de contrôle ActiveX non pris en charge. Vous pouvez migrer des contrôles existants vers Visual Studio si vous êtes le propriétaire du code source d’origine. Dans le cas contraire, vous pouvez consulter les éditeurs de logiciels pour les mettre à jour. Versions compatibles NET des contrôles pour remplacer les contrôles ActiveX non pris en charge.  
  
## <a name="vbconinteroperabilitymarshalinganchor11"></a>Passage de propriétés ReadOnly de contrôles ByRef  
 Visual Basic .NET génère parfois des erreurs com, telles que «Error 0x800A017F CTL_E_SETNOTSUPPORTED», lorsque vous `ReadOnly` transmettez des propriétés de certains contrôles `ByRef` ActiveX plus anciens en tant que paramètres à d’autres procédures. Des appels de procédure similaires à partir de Visual Basic 6,0 ne génèrent pas d’erreur et les paramètres sont traités comme si vous les aviez passés par valeur. Le message d’erreur Visual Basic .net indique que vous essayez de modifier une propriété qui n’a pas de procédure `Set` de propriété.  
  
 Si vous avez accès à la procédure appelée, vous pouvez éviter cette erreur en utilisant le mot `ByVal` clé pour déclarer les paramètres qui `ReadOnly` acceptent des propriétés. Par exemple :  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Si vous n’avez pas accès au code source de la procédure appelée, vous pouvez forcer la propriété à être passée par valeur en ajoutant un ensemble de crochets supplémentaires autour de la procédure appelante. Par exemple, dans un projet qui a une référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2,8, vous pouvez utiliser:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="vbconinteroperabilitymarshalinganchor12"></a>Déploiement d’assemblys qui exposent l’interopérabilité  
 Le déploiement d’assemblys qui exposent des interfaces COM présente des défis uniques. Par exemple, un problème potentiel se produit lorsque des applications distinctes référencent le même assembly COM. Cette situation est courante lorsqu’une nouvelle version d’un assembly est installée et qu’une autre application utilise toujours l’ancienne version de l’assembly. Si vous désinstallez un assembly qui partage une DLL, vous pouvez involontairement le rendre inaccessible aux autres assemblys.  
  
 Pour éviter ce problème, vous devez installer les assemblys partagés dans le global assembly cache (GAC) et utiliser un MergeModule pour le composant. Si vous ne pouvez pas installer l’application dans le GAC, elle doit être installée dans CommonFilesFolder dans un sous-répertoire spécifique à la version.  
  
 Les assemblys qui ne sont pas partagés doivent être situés côte à côte dans le répertoire avec l’application appelante.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importateur de bibliothèques de types)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportateur de bibliothèques de types)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Global Assembly Cache](../../../framework/app-domains/gac.md)
