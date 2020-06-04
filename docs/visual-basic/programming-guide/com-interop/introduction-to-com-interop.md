---
title: Présentation de COM Interop
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 6c7caf266514c43e40135b33d848a688546acf1c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396777"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Introduction à COM Interop (Visual Basic)
Le modèle COM (Component Object Model) permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Bien que les objets COM soient fondamentaux pour la programmation Windows depuis de nombreuses années, les applications conçues pour le common language runtime (CLR) offrent de nombreux avantages.  
  
 .NET Framework applications remplacent éventuellement celles développées avec COM. Jusqu’à présent, vous devrez peut-être utiliser ou créer des objets COM à l’aide de Visual Studio. L’interopérabilité avec COM, ou *COM Interop*, vous permet d’utiliser des objets COM existants lors de la transition vers le .NET Framework à votre propre rythme.  
  
 En utilisant l' .NET Framework pour créer des composants COM, vous pouvez utiliser des COM Interop sans inscription. Cela vous permet de contrôler la version de DLL qui est activée lorsque plusieurs versions sont installées sur un ordinateur, et permet aux utilisateurs finaux d’utiliser XCOPY ou FTP pour copier votre application dans un répertoire approprié sur son ordinateur où elle peut être exécutée. Pour plus d’informations, consultez [COM Interop sans inscription](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Code managé et données  
 Le code développé pour le .NET Framework est appelé *code managé*et contient les métadonnées utilisées par le CLR. Les données utilisées par les applications .NET Framework sont appelées *données managées* car le Runtime gère les tâches liées aux données, telles que l’allocation et la récupération de la mémoire et l’exécution de la vérification de type. Par défaut, Visual Basic .NET utilise du code managé et des données, mais vous pouvez accéder au code non managé et aux données d’objets COM à l’aide d’assemblys d’interopérabilité (décrits plus loin dans cette page).  
  
## <a name="assemblies"></a>Assemblys  
 Un assembly est le bloc de construction principal d’une application .NET Framework. Il s’agit d’une collection de fonctionnalités générées, gérées par version et déployées comme une seule unité d’implémentation contenant un ou plusieurs fichiers. Chaque assembly contient un manifeste d’assembly.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Bibliothèques de types et manifestes d’assembly  
 Les bibliothèques de types décrivent les caractéristiques des objets COM, tels que les noms de membres et les types de données. Les manifestes d’assembly exécutent la même fonction pour .NET Framework applications. Ils incluent des informations sur les éléments suivants :  
  
- L’identité de l’assembly, la version, la culture et la signature numérique.  
  
- Fichiers qui composent l’implémentation de l’assembly.  
  
- Types et ressources qui composent l’assembly. Cela comprend ceux qui sont exportés à partir de celui-ci.  
  
- Dépendances au moment de la compilation sur d’autres assemblys.  
  
- Autorisations requises pour que l’assembly s’exécute correctement.  
  
 Pour plus d’informations sur les assemblys et les manifestes d’assembly, consultez [assemblys dans .net](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importation et exportation de bibliothèques de types  
 Visual Studio contient un utilitaire, Tlbimp, qui vous permet d’importer des informations à partir d’une bibliothèque de types dans une application .NET Framework. Vous pouvez générer des bibliothèques de types à partir d’assemblys à l’aide de l’utilitaire Tlbexp.  
  
 Pour plus d’informations sur Tlbimp et Tlbexp, consultez [Tlbimp. exe (importateur de bibliothèques de types)](../../../framework/tools/tlbimp-exe-type-library-importer.md) et [Tlbexp. exe (exportateur de bibliothèques de types)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Assemblys d’interopérabilité  
 Les assemblys d’interopérabilité sont des assemblys .NET Framework qui font l’objet d’un pont entre du code managé et du code non managé, en mappant des membres d’objets COM à des membres .NET Framework gérés équivalents. Les assemblys d’interopérabilité créés par Visual Basic .NET gèrent un grand nombre des détails de l’utilisation des objets COM, tels que le marshaling d’interopérabilité.  
  
## <a name="interoperability-marshaling"></a>Marshaling d’interopérabilité  
 Toutes les applications .NET Framework partagent un ensemble de types communs qui permettent l’interopérabilité des objets, quel que soit le langage de programmation utilisé. Les paramètres et les valeurs de retour des objets COM utilisent parfois des types de données qui diffèrent de ceux utilisés dans le code managé. Le *marshaling d’interopérabilité* est le processus d’empaquetage de paramètres et de valeurs de retour dans des types de données équivalents lorsqu’ils sont déplacés vers et à partir d’objets com. Pour plus d’informations, consultez la page [marshaling d’interopérabilité](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Voir aussi

- [COM Interop](index.md)
- [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [Interopération avec du code non managé](../../../framework/interop/index.md)
- [Dépannage de l’interopérabilité](troubleshooting-interoperability.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Tlbimp. exe (importateur de bibliothèques de types)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp. exe (exportateur de bibliothèques de types)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Marshaling d’interopérabilité](../../../framework/interop/interop-marshaling.md)
- [COM Interop sans inscription](../../../framework/interop/registration-free-com-interop.md)
