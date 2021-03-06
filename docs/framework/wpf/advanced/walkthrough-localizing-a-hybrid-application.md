---
title: 'Procédure pas à pas : localisation d’une application hybride'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b98bf7b3f0aa4e7698a5c0ca7c8ae16051ce6300
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991778"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Procédure pas à pas : localisation d’une application hybride

Cette procédure pas à pas vous montre comment [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localiser des éléments [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]dans une application hybride basée sur.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projet hôte.

- Ajout de contenu localisable

- Activation de la localisation

- Assignation d’identificateurs de ressource

- Utilisation de l’outil LocBaml pour produire un assembly satellite

Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [localisation d’un exemple d’application hybride](https://go.microsoft.com/fwlink/?LinkID=160015).

Quand vous aurez terminé, vous disposerez d’une application hybride localisée.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Création du projet hôte Windows Forms

La première étape consiste à créer le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projet d’application et à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ajouter un élément avec le contenu que vous allez localiser.

### <a name="to-create-the-host-project"></a>Pour créer le projet hôte

1. Créez un projet d' **application WPF** nommé `LocalizingWpfInWf`.  (**Fichier** > **nouveau** > **projet**visuelouVisualBasic > **application WPF**de**Bureau classique)** .**C#**  >  > 

2. Ajoutez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> élément appelé`SimpleControl` au projet.

3. Utilisez le <xref:System.Windows.Forms.Integration.ElementHost> contrôle pour placer un `SimpleControl` élément sur le formulaire. Pour plus d’informations, consultez [Procédure pas à pas : Hébergement d’un contrôle composite 3D WPF dans Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Ajout de contenu localisable

Ensuite, vous allez ajouter un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle Label et définir le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu de l’élément sur une chaîne localisable.

### <a name="to-add-localizable-content"></a>Pour ajouter du contenu localisable

1. Dans **Explorateur de solutions**, double-cliquez sur **SimpleControl. Xaml** pour l’ouvrir dans [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]le.

2. Définissez le contenu du <xref:System.Windows.Controls.Button> contrôle à l’aide du code suivant.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. Dans **Explorateur de solutions**, double-cliquez sur **Form1** pour l’ouvrir dans le Concepteur Windows Forms.

4. Ouvrez la **boîte à outils** et double-cliquez sur **étiquette** pour ajouter un contrôle Label au formulaire. Affectez à sa propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `"Hello"`.

5. Appuyez sur **F5** pour générer et exécuter l’application.

     L' `SimpleControl` élément et le contrôle Label affichent le texte **« Hello »** .

## <a name="enabling-localization"></a>Activation de la localisation

Le Concepteur Windows Forms comprend des paramètres permettant d’activer la localisation dans un assembly satellite.

### <a name="to-enable-localization"></a>Pour activer la localisation

1. Dans **Explorateur de solutions**, double-cliquez sur **Form1.cs** pour l’ouvrir dans le Concepteur Windows Forms.

2. Dans la fenêtre **Propriétés** , définissez la valeur de la propriété **localisable** du formulaire sur `true`.

3. Dans la fenêtre **Propriétés** , définissez la valeur de la propriété **Language** sur **espagnol (Espagne)** .

4. Dans le Concepteur Windows Forms, sélectionnez le contrôle d’étiquette.

5. Dans la fenêtre **Propriétés** , affectez à <xref:System.Windows.Forms.Control.Text%2A> `"Hola"`la propriété la valeur.

     Un nouveau fichier de ressources nommé Form1.es-ES.resx est ajouté au projet.

6. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs** , puis cliquez sur **afficher le code** pour l’ouvrir dans l’éditeur de code.

7. Copiez le code suivant dans `Form1` le constructeur, avant l’appel `InitializeComponent`à.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **LocalizingWpfInWf** , puis cliquez sur **décharger le projet**.

     Le nom du projet est étiqueté **(non disponible)** .

9. Cliquez avec le bouton droit sur **LocalizingWpfInWf**, puis cliquez sur **modifier LocalizingWpfInWf. csproj**.

     Le fichier projet s’ouvre dans l’éditeur de code.

10. Copiez la ligne suivante dans le `PropertyGroup` premier dans le fichier projet.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Enregistrez, puis fermez le fichier projet.

12. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **LocalizingWpfInWf** , puis cliquez sur **recharger le projet**.

## <a name="assigning-resource-identifiers"></a>Assignation d’identificateurs de ressource

Vous pouvez mapper votre contenu localisable à des assemblys de ressources en utilisant des identificateurs de ressource. L’application MSBuild. exe assigne automatiquement des identificateurs de ressource lorsque vous `updateuid` spécifiez l’option.

### <a name="to-assign-resource-identifiers"></a>Pour assigner des identificateurs de ressource

1. Dans le menu Démarrer, ouvrez le Invite de commandes développeur pour Visual Studio.

2. Utilisez la commande suivante pour assigner des identificateurs de ressource à votre contenu localisable.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. Dans **Explorateur de solutions**, double-cliquez sur **SimpleControl. Xaml** pour l’ouvrir dans l’éditeur de code. Vous verrez que la `msbuild` commande a ajouté l' `Uid` attribut à tous les éléments. Cela facilite la localisation par l’assignation des identificateurs de ressource.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Appuyez sur **F6** pour générer la solution.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Utilisation de LocBaml pour produire un assembly satellite

Votre contenu localisé est stocké dans un *assembly satellite*de ressources uniquement. Utilisez l’outil en ligne de commande LocBaml. exe pour générer un assembly localisé pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] votre contenu.

### <a name="to-produce-a-satellite-assembly"></a>Pour produire un assembly satellite

1. Copiez LocBaml.exe dans le dossier obj\Debug de votre projet. Pour plus d’informations, consultez [localiser une application](how-to-localize-an-application.md).

2. Dans la fenêtre d’invite de commandes, utilisez la commande suivante pour extraire les chaînes de ressources dans un fichier temporaire.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Ouvrez le fichier Temp. csv avec Visual Studio ou un autre éditeur de texte. Remplacez la chaîne `"Hello"` par sa traduction espagnole, `"Hola"`.

4. Enregistrez le fichier temp.csv.

5. Utilisez la commande suivante pour générer le fichier de ressources localisé.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Le fichier LocalizingWpfInWf.g.es-ES.resources est créé dans le dossier obj\Debug.

6. Utilisez la commande suivante pour générer l’assembly satellite localisé.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Le fichier LocalizingWpfInWf.resources.dll est créé dans le dossier obj\Debug.

7. Copiez le fichier LocalizingWpfInWf.resources.dll dans le dossier du projet bin\Debug\es-ES. Remplacez le fichier existant.

8. Exécutez LocalizingWpfInWf.exe, qui se trouve dans le dossier bin\Debug de votre projet. Ne regénérez pas l’application, car cela aura pour effet de remplacer l’assembly satellite.

     L’application affiche les chaînes localisées au lieu des chaînes en anglais.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Localiser une application](how-to-localize-an-application.md)
- [Procédure pas à pas : Localisation de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
