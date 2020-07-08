---
title: 'Comment : effectuer une compilation conditionnelle avec Trace et Debug'
description: Découvrez comment effectuer une compilation conditionnelle avec les attributs conditionnels de TRACE et de débogage lors de la compilation d’une application .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
ms.openlocfilehash: 8758b793866ec0317f91d636476d33bd001ddd78
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051218"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Comment : effectuer une compilation conditionnelle avec Trace et Debug
Quand vous déboguez une application pendant le développement, les sorties de débogage et de traçage sont dirigées vers la fenêtre de sortie dans Visual Studio. Toutefois, pour inclure les fonctionnalités de suivi dans une application déployée, vous devez compiler vos applications instrumentées en activant la directive de compilateur **TRACE**. De cette façon, le code de traçage peut être compilé dans la version commerciale de votre application. Si vous n’activez pas la directive **TRACE**, tout le code de suivi est ignoré pendant la compilation et n’est pas inclus dans le code exécutable que vous déployez.  
  
 Les méthodes de traçage et de débogage sont associées à des attributs conditionnels. Par exemple, si l’attribut conditionnel pour le suivi a la valeur **true**, toutes les instructions de suivi sont incluses dans un assembly (fichier .exe ou .dll compilé) ; si l’attribut conditionnel **Trace** a la valeur **false**, les instructions de suivi ne sont pas incluses.  
  
 Vous pouvez activer l’attribut conditionnel **Trace** ou **Debug**, les deux ou aucun pour une build. Par conséquent, il existe quatre types de build : **Debug**, **Trace**, les deux ou aucun. Certaines versions release pour un déploiement de production peuvent n'en contenir aucun, mais la plupart des builds contiennent les deux.  
  
 Vous pouvez spécifier les paramètres du compilateur pour votre application de plusieurs façons :  
  
- Pages de propriétés  
  
- Ligne de commande  
  
- **#CONST** (pour Visual Basic) et **#define** (pour C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Pour modifier les paramètres de compilation dans la boîte de dialogue des pages de propriétés  
  
1. Cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**.  
  
2. Choisissez **Propriétés** dans le menu contextuel.  
  
    - En Visual Basic, cliquez sur l’onglet **Compiler** dans le volet gauche de la page de propriétés, puis sur le bouton **Options avancées de compilation** pour afficher la boîte de dialogue **Paramètres avancés du compilateur**. Cochez les cases des paramètres du compilateur que vous voulez activer. Décochez les cases des paramètres que vous voulez désactiver.  
  
    - En C#, cliquez sur l’onglet **Générer** dans le volet gauche de la page de propriétés, puis cochez les cases des paramètres du compilateur que vous voulez activer. Décochez les cases des paramètres que vous voulez désactiver.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Pour compiler du code instrumenté à l'aide de la ligne de commande  
  
1. Définissez un commutateur de compilateur conditionnel sur la ligne de commande. Le compilateur devra contenir du code de traçage ou de débogage dans l'exécutable.  
  
     Par exemple, l'instruction de compilateur suivante entrée sur la ligne de commande inclut le code de traçage dans un fichier exécutable compilé :  
  
     Pour Visual Basic : **vbc -r:System.dll-d :trace = true-d :debug = False MyApplication. vb**  
  
     Pour C# : **csc -r:System.dll-d :trace-d :Debug = false MyApplication.cs**  
  
    > [!TIP]
    > Pour compiler plusieurs fichiers d’application, insérez un espace entre les noms de fichiers, par exemple **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     La signification des directives de compilation conditionnelle utilisées dans les exemples ci-dessus est la suivante :  
  
    |Directive|Signification|  
    |---------------|-------------|  
    |`vbc`|compilateur Visual Basic|  
    |`csc`|Compilateur C#|  
    |`-r:`|Référence un assembly externe (EXE ou DLL)|  
    |`-d:`|Définit un symbole de compilation conditionnelle|  
  
    > [!NOTE]
    > Vous devez écrire TRACE ou DEBUG en majuscules. Pour plus d'informations sur les commandes de compilation conditionnelle, entrez `vbc /?` (pour Visual Basic) ou `csc /?` (pour C#) à l'invite de commandes. Pour plus d’informations, consultez [Génération à partir de la ligne de commande](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Appel du compilateur de ligne de commande](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>Pour effectuer une compilation conditionnelle à l'aide de #CONST ou #define  
  
1. Tapez l'instruction appropriée pour votre langage de programmation en haut du fichier de code source.  
  
    |Langage|.|Résultats|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST TRACE = true**|Active le traçage|  
    ||**#CONST TRACE = false**|Désactive le traçage|  
    ||**#CONST DEBUG = true**|Active le débogage|  
    ||**#CONST DEBUG = false**|Désactive le débogage|  
    |**C#**|**#define TRACE**|Active le traçage|  
    ||**#undef TRACE**|Désactive le traçage|  
    ||**#define DEBUG**|Active le débogage|  
    ||**#undef DEBUG**|Désactive le débogage|  
  
### <a name="to-disable-tracing-or-debugging"></a>Pour désactiver le traçage ou le débogage  
  
Supprimez la directive de compilateur de votre code source.  
  
\- ou -  
  
Commentez la directive de compilateur.  
  
> [!NOTE]
> Quand vous êtes prêt pour la compilation, vous pouvez choisir **Générer** dans le menu **Générer**, ou utiliser la méthode de ligne de commande, mais sans taper **d:** pour définir les symboles de compilation conditionnelle.  
  
## <a name="see-also"></a>Voir aussi

- [Traçage et instrumentation d'applications](tracing-and-instrumenting-applications.md)
- [Comment : créer, initialiser et configurer les commutateurs de traçage](how-to-create-initialize-and-configure-trace-switches.md)
- [Commutateurs de traçage](trace-switches.md)
- [Écouteurs de suivi](trace-listeners.md)
- [Comment : ajouter des instructions de traçage dans le code d'une application](how-to-add-trace-statements-to-application-code.md)
- [Comment : définir des variables d’environnement pour la ligne de commande Visual Studio](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [Procédure : Appeler le compilateur de ligne de commande](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
