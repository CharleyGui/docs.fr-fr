---
title: 'Procédure : Générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971836"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Procédure : Générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires

## <a name="applies-to"></a>S'applique à

- Microsoft® Windows® Identity Foundation (WIF)

- Web Forms ASP.NET®

## <a name="summary"></a>Récapitulatif

Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application Web Forms ASP.NET prenant en charge les revendications et utilisant l’authentification par formulaire. Elle fournit également des instructions pour tester l’application afin de vérifier que les revendications s’affichent quand un utilisateur se connecte à l’aide de l’authentification par formulaire.

## <a name="contents"></a>Sommaire

- Objectifs

- Présentation

- Résumé des étapes

- Étape 1 : Créer une application Web Forms ASP.NET simple

- Étape 2 : Configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire

- Étape 3 : tester votre solution

## <a name="objectives"></a>Objectifs

- Configurer une application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire

- Tester l’application Web Forms ASP.NET pour vérifier si elle fonctionne correctement

## <a name="overview"></a>Présentation

Dans .NET 4.5, WIF et son autorisation basée sur les revendications ont été ajoutés en tant que partie intégrante du .NET Framework. Auparavant, si vous vouliez obtenir des revendications d’un utilisateur ASP.NET, vous deviez installer WIF et convertir les interfaces en objets Entité de sécurité tels que `Thread.CurrentPrincipal` ou `HttpContext.Current.User`. À présent, les revendications sont prises en charge automatiquement par ces objets Entité de sécurité.

L’authentification par formulaire a bénéficié de l’ajout de WIF dans .NET 4.5, car tous les utilisateurs authentifiés par des formulaires sont automatiquement associés à des revendications. Vous pouvez commencer à utiliser ces revendications immédiatement dans une application ASP.NET qui utilise l’authentification par formulaire, comme l’illustre cette procédure.

## <a name="summary-of-steps"></a>Résumé des étapes

- Étape 1 : Créer une application Web Forms ASP.NET simple

- Étape 2 : Configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire

- Étape 3 : tester votre solution

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Étape 1 : Créer une application Web Forms ASP.NET simple

Lors de cette étape, vous allez créer une application Web Forms ASP.NET.

### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une simple application ASP.NET

1. Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.

2. Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.

3. Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Étape 2 : Configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire

Lors de cette étape, vous allez ajouter une entrée de configuration au fichier de configuration *Web.config* et modifier le fichier *Default.aspx* pour afficher les informations sur les revendications d’un compte.

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Pour configurer une application ASP.NET pour les revendications à l’aide de l’authentification par formulaire

1. Dans le fichier *Default.aspx*, remplacez le balisage existant par le code suivant :

    ```aspx
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Forms authenticated user.
        </p>
        <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

    Cette étape ajoute un contrôle GridView à votre page *Default.aspx* qui sera remplie avec les revendications récupérées à partir de l’authentification par formulaire.

2. Enregistrez le fichier *Default.aspx*, puis ouvrez son fichier code-behind nommé *Default.aspx.cs*. Remplacez le code existant par le code ci-dessous :

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;

                if (claimsPrincipal != null)
                {
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                    this.ClaimsGridView.DataBind();
                }
            }
        }
    }
    ```

    Le code ci-dessus affiche les revendications relatives à un utilisateur authentifié, y compris les utilisateurs identifiés par l’authentification par formulaire.

## <a name="step-3--test-your-solution"></a>Étape 3 : tester votre solution

Dans cette étape, vous allez tester votre application Web Forms ASP.NET et vérifier que les revendications sont présentées à l’utilisateur qui se connecte à l’aide de l’authentification par formulaire.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Pour tester votre application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire

1. Appuyez sur **F5** pour générer et exécuter l’application. La page *Default.aspx* doit s’afficher, avec des liens **Register** et **Log in** en haut à droite. Cliquez sur **Register**.

2. Dans la page **Register**, créez un compte d’utilisateur, puis cliquez sur **Register**. Votre compte sera créé à l’aide de l’authentification par formulaire, et vous serez connecté automatiquement.

3. Après avoir été redirigé vers la page d’accueil, vous devriez voir sous l’en-tête **Your Claims** une table qui inclut les informations de revendications **Issuer**, **OriginalIssuer**, **Type**, **Value** et **ValueType** relatives à votre compte.
