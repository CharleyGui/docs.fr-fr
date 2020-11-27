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
ms.openlocfilehash: 01cbfeb72e19f727a3a470059047a2192228c394
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293856"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a><span data-ttu-id="f2cce-103">wfc.exe (outil du compilateur de ligne de commande du flux de travail)</span><span class="sxs-lookup"><span data-stu-id="f2cce-103">wfc.exe (Workflow Command-line Compiler Tool)</span></span>

> [!NOTE]
> <span data-ttu-id="f2cce-104">Ce document décrit les types et les espaces de noms qui sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="f2cce-104">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="f2cce-105">L’outil de compilateur de ligne de commande wfc.exe workflow fonctionne avec les anciens fichiers de balisage de workflow qui ont l’extension de fichier *. xoml* (obsolète).</span><span class="sxs-lookup"><span data-stu-id="f2cce-105">The wfc.exe workflow command-line compiler tool works with old workflow markup files that have the file extension *.xoml* (obsoleted).</span></span>

## <a name="compilation-process"></a><span data-ttu-id="f2cce-106">Processus de compilation</span><span class="sxs-lookup"><span data-stu-id="f2cce-106">Compilation process</span></span>

<span data-ttu-id="f2cce-107">Lorsque les workflows sont compilés, les procédures suivantes sont effectuées dans le cadre du processus de compilation :</span><span class="sxs-lookup"><span data-stu-id="f2cce-107">When workflows are compiled, the following procedures are performed as part of the compilation process:</span></span>

- <span data-ttu-id="f2cce-108">La validation est effectuée pour s'assurer que les activités de flux de travail sont validées selon les règles que les activités ont établies pour elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="f2cce-108">Validation is performed to ensure that the workflow activities validate based on the rules that the activities have set for themselves.</span></span> <span data-ttu-id="f2cce-109">En cas d'erreurs de validation, le compilateur retourne une liste des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f2cce-109">If there are validation errors, the compiler returns a list of the errors.</span></span>  
- <span data-ttu-id="f2cce-110">Une classe partielle est générée par la définition de balise entrée dans le compilateur.</span><span class="sxs-lookup"><span data-stu-id="f2cce-110">A partial class is generated from the markup definition that is input into the compiler.</span></span>  

- <span data-ttu-id="f2cce-111">Le code est généré pour faciliter l'exécution du runtime des activités.</span><span class="sxs-lookup"><span data-stu-id="f2cce-111">Code is generated to help with the run-time execution of the activities.</span></span> <span data-ttu-id="f2cce-112">Les abonnements d'événement sont générés, afin de permettre aux activités de savoir quand les activités qu'elles contiennent auront terminé de s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="f2cce-112">Event subscriptions are generated, which help activities know when the activities they contain are finished executing.</span></span>  
- <span data-ttu-id="f2cce-113">Les classes partielles générées par le fichier de balisage et les classes partielles du fichier de code sont introduites dans le compilateur C# ou Visual Basic du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2cce-113">The partial classes generated from the markup file and the partial classes from the code file are entered into the .NET Framework C# or Visual Basic compiler.</span></span> <span data-ttu-id="f2cce-114">La sortie de ce processus est l'assembly .NET, WorkflowSample.dll.</span><span class="sxs-lookup"><span data-stu-id="f2cce-114">The output of this process is the .NET assembly, WorkflowSample.dll.</span></span> <span data-ttu-id="f2cce-115">Ceci peut être déployé en vue d'exécuter le workflow.</span><span class="sxs-lookup"><span data-stu-id="f2cce-115">This can be deployed to run the workflow.</span></span>

### <a name="compiler-options"></a><span data-ttu-id="f2cce-116">Options du compilateur</span><span class="sxs-lookup"><span data-stu-id="f2cce-116">Compiler options</span></span>

<span data-ttu-id="f2cce-117">Cette section présente les options du compilateur de ligne de commande du flux de travail wfc.exe.</span><span class="sxs-lookup"><span data-stu-id="f2cce-117">This section shows the options for the wfc.exe workflow command-line compiler.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="f2cce-118">Notes</span><span class="sxs-lookup"><span data-stu-id="f2cce-118">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="f2cce-119">Ce document décrit les types et les espaces de noms qui sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="f2cce-119">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="f2cce-120">Une liste de types autorisés est généralement définie dans le fichier *wfc.exe.config* .</span><span class="sxs-lookup"><span data-stu-id="f2cce-120">A list of authorized types is usually defined in the *wfc.exe.config* file.</span></span> <span data-ttu-id="f2cce-121">Pendant la phase de validation de la compilation du workflow, un document source de workflow est rejeté si celui-ci ou le fichier de règles d’accompagnement fait directement référence à tous les types de .NET Framework absents de la liste des types autorisés.</span><span class="sxs-lookup"><span data-stu-id="f2cce-121">During the validation phase of workflow compilation, a workflow source document is rejected if it or the companion rules file directly references any .NET Framework types not present in a list of authorized types.</span></span> <span data-ttu-id="f2cce-122">La liste des types autorisés est un document XML où chaque entrée indique un `Assembly` , un `Namespace` , un `TypeName` et un `True` indicateur {&#124;`False` } autorisé.</span><span class="sxs-lookup"><span data-stu-id="f2cce-122">The list of authorized types is an XML document where each entry indicates an `Assembly`, a `Namespace`, a `TypeName`, and an Authorized {`True`&#124;`False`} indicator.</span></span> <span data-ttu-id="f2cce-123">`AuthorizedType` correspond à une entrée de la liste.</span><span class="sxs-lookup"><span data-stu-id="f2cce-123">`AuthorizedType` corresponds to an entry in the list.</span></span> <span data-ttu-id="f2cce-124">Les désignations de caractères génériques, qui peuvent être utilisées pour inclure ou exclure des espaces de noms complets, sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="f2cce-124">Wildcard character designations, which can be used to include or exclude complete namespaces, are allowed.</span></span> <span data-ttu-id="f2cce-125">Par exemple, `Type="System.*"` inclut tous les types dans <xref:System> , y compris les types contenus dans les espaces de noms enfants.</span><span class="sxs-lookup"><span data-stu-id="f2cce-125">For example, `Type="System.*"` includes all types in <xref:System>, including types contained in child namespaces.</span></span>
  
<span data-ttu-id="f2cce-126">L’utilisation d’une liste de types autorisés est contrôlée par l' <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'` .</span><span class="sxs-lookup"><span data-stu-id="f2cce-126">The use of a list of authorized types is controlled by the <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'`.</span></span>

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
> <span data-ttu-id="f2cce-127">Quand `Type="System.*"` le type est présent, il est possible d’inclure d’autres types involontaires, tels que `Type="System.Configuration"` , pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="f2cce-127">When `Type="System.*"` type is present, it's possible to include other unintended types, such as `Type="System.Configuration"`, for compilation.</span></span> <span data-ttu-id="f2cce-128">Soyez prudent et passez en revue chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="f2cce-128">You should be cautious and review each one.</span></span> <span data-ttu-id="f2cce-129">Pour tous les types qui doivent être restreints, veillez à affecter à la valeur `Authorized` `False` .</span><span class="sxs-lookup"><span data-stu-id="f2cce-129">For any type that should be restricted, be sure to set `Authorized` to `False`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2cce-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2cce-130">See also</span></span>

- [<span data-ttu-id="f2cce-131">AuthorizedType, classe</span><span class="sxs-lookup"><span data-stu-id="f2cce-131">AuthorizedType class</span></span>](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
