---
title: Wfc.exe (outil du compilateur de ligne de commande du flux de travail)
description: Comprendre wfc.exe, l’outil de compilateur de ligne de commande de flux de travail.
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: cf89962014584adf098118044b063b38b29160b7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844602"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a>wfc.exe (outil du compilateur de ligne de commande du flux de travail)
> [!NOTE]
> Ce document décrit les types et les espaces de noms qui sont obsolètes.

L’outil de compilateur de ligne de commande wfc.exe workflow fonctionne avec les anciens fichiers de balisage de workflow qui ont l’extension de fichier *. xoml* (obsolète).

## <a name="compilation-process"></a>Processus de compilation

Lorsque les workflows sont compilés, les procédures suivantes sont effectuées dans le cadre du processus de compilation :

- La validation est effectuée pour s'assurer que les activités de flux de travail sont validées selon les règles que les activités ont établies pour elles-mêmes. En cas d'erreurs de validation, le compilateur retourne une liste des erreurs.  
- Une classe partielle est générée par la définition de balise entrée dans le compilateur.  

- Le code est généré pour faciliter l'exécution du runtime des activités. Les abonnements d'événement sont générés, afin de permettre aux activités de savoir quand les activités qu'elles contiennent auront terminé de s'exécuter.  
- Les classes partielles générées par le fichier de balisage et les classes partielles du fichier de code sont introduites dans le compilateur C# ou Visual Basic du .NET Framework. La sortie de ce processus est l'assembly .NET, WorkflowSample.dll. Ceci peut être déployé en vue d'exécuter le workflow.

### <a name="compiler-options"></a>Options du compilateur

Cette section présente les options du compilateur de ligne de commande du flux de travail wfc.exe.

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a>Notes
> [!NOTE]
> Ce document décrit les types et les espaces de noms qui sont obsolètes.

Une liste de types autorisés est généralement définie dans le fichier *wfc.exe.config* . Pendant la phase de validation de la compilation du workflow, un document source de workflow est rejeté si celui-ci ou le fichier de règles d’accompagnement fait directement référence à tous les types de .NET Framework absents de la liste des types autorisés. La liste des types autorisés est un document XML où chaque entrée indique un `Assembly` , un `Namespace` , un `TypeName` et un `True` indicateur {&#124;`False` } autorisé. `AuthorizedType` correspond à une entrée de la liste. Les désignations de caractères génériques, qui peuvent être utilisées pour inclure ou exclure des espaces de noms complets, sont autorisées. Par exemple, `Type="System.*"` inclut tous les types dans <xref:System> , y compris les types contenus dans les espaces de noms enfants.
  
L’utilisation d’une liste de types autorisés est contrôlée par l' <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'` .

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> Quand `Type="System.*"` le type est présent, il est possible d’inclure d’autres types involontaires, tels que `Type="System.Configuration"` , pour la compilation. Soyez prudent et passez en revue chacune d’elles. Pour tous les types qui doivent être restreints, veillez à affecter à la valeur `Authorized` `False` .

## <a name="see-also"></a>Voir aussi

- [AuthorizedType, classe](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
