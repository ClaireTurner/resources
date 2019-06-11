---

copyright:
  years: 2017, 2019
lastupdated: "2019-05-13"

keywords: change service, upgrade service, service plan, pricing plan

subcollection: account

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}


# Servicepläne ändern
{: #changing}

Sie können den Preistarif eines {{site.data.keyword.Bluemix}}-Service ändern, wenn für diesen einen Service Planänderungen aktiviert sind. Der Tarif kann beispielsweise geändert werden, um ein Upgrade durchzuführen oder um zu einem Plan mit weniger Features zu wechseln. Sie können den Preistarif des Service über das Dashboard der Serviceinstanz ändern.
{: shortdesc}

Sind Sie auf der Suche nach Details zum Upgrade Ihres Kontotyps? Weitere Informationen finden Sie in [Upgrade für das Konto durchführen](/docs/account?topic=account-upgrading-account).
{: tip}

Das Ändern der Servicepläne ist nur für bestimmte Services möglich. Wenn Planänderungen für den Service aktiviert sind, wird im Serviceinstanzdashboard die Option **Plan** im Navigationsbereich angezeigt. Für jeden Service müssen unterschiedliche weitere Schritte ausgeführt werden, wenn Sie Ihren Plan ändern.

1. Klicken Sie in der {{site.data.keyword.Bluemix_notm}}-Konsole auf das Menüsymbol ![Menüsymbol](../icons/icon_hamburger.svg) und dann auf **Ressourcenliste**, um Ihre Ressourcenliste anzuzeigen. Klicken Sie auf den Service, den Sie aktualisieren möchten.
1. Klicken Sie im Dashboard der Serviceinstanz auf **Plan**. Wählen Sie den Plan aus, zu dem Sie wechseln möchten, und klicken Sie auf **Speichern**.

    Einige Services verfügen über Pläne, die nicht über die Seite 'Plan' ausgewählt werden können. Typischerweise sind diese Pläne nicht auswählbar, weil sie Unterstützung vom Vertriebsteam erforderlich machen oder weil eine Migration ausgeführt werden muss, bevor Sie Pläne ändern können. Informationen zu den erforderlichen nächsten Schritten finden Sie in der Dokumentation.

1. Nach dem Ändern des Plans müssen Sie zusätzliche Schritte ausführen. Die Schritte variieren abhängig von der Art der Planänderung und vom Service. Wenn Sie beispielsweise Ihren Plan reduziert haben, müssen Sie möglicherweise ein erneutes Staging für Ihre App durchführen. Oder wenn Sie für Ihren Plan ein Upgrade durchgeführt haben, müssen Sie möglicherweise ein erneutes Staging für Ihre App und weitere Aktionen durchführen.

   Für ein erneutes Staging Ihrer App rufen Sie die Ressourcenliste auf und suchen Sie nach der App, an die der Service gebunden ist. Klicken Sie auf das Menüsymbol ![Menüsymbol](../icons/icon_hamburger.svg) ** und dann auf Ressourcenliste**. Wählen Sie im Menü 'App' die Option **Anwendung erneut starten** aus.

  Weitere Informationen zu weiteren erforderlichen Aktionen finden Sie in der Dokumentation für den Service.

## Plan über die CLI ändern
{: #changing_command_line}

Als Alternative zur Konsole können Sie den Preistarif eines Service über die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle (CLI) ändern.

1. Prüfen Sie, ob der Service mit dem Ressourcencontroller aktiviert ist.

   ```
   ibmcloud catalog service <servicename>
   ```
   {:codeblock}

   Wenn der Service mit dem Ressourcencontroller (RC) aktiviert ist, listet er `RC Compatible true` auf. Vermerken Sie die ID des Plans, zu dem Sie wechseln möchten.

   ```
   RC Compatible      true
   RC Provisionable   true
   IAM Compatible     true
   Children   Name                      Kind         ID
              lite                      plan         4bcd3fgh-3cf2-47c0-93d4-d2f2289eac28
              standard                  plan         264d0450-996d-4bcd-894d-fc7018dacf1e
    ```

1. Ändern Sie den Plan für Ihre Serviceinstanz.

   - Wenn der Service RC-fähig ist, können Sie Ihren Plan mit dem [Befehl `ibmcloud resource service-instance-update`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_update) ändern. 

     ```
     ibmcloud resource service-instance-update <service_instance_name> --service-plan-id <plan_id>
     ```
     {: codeblock}

   - Wenn der Service nicht RC-fähig ist und daher auf Cloud Foundry basiert, können Sie Ihren Plan mithilfe des [Befehls `ibmcloud cf update-service`](/docs/cli?topic=cloud-cli-ibmcloud_commands_services#ibmcloud_service_update) ändern.

     ```
     ibmcloud cf update-service <service_instance_name> [-p <plan_name>]
     ```
     {:codeblock}
