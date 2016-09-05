# SapUi5CreateExampleRouting
I'm createt it for help you create SAP UI routing

We will use roting between view1.xml and view2.xml.

Step 1 – use tag APP

Create a tag <App> in view1.xml. It will be container for yourcontent.
  <App id="app" width="100%">
</App>

Step 2 – change view1.controller

		to_view2: function(oEvent) {
			//	this.getRouter().navTo("page2");

			var ch = this.getView().byId('inputview1').getValue();
			this.getRouter().navTo("to_view2", {
				idtranzaction: ch
			});
		},
Step 3 – change your manifest

	"routing": {
			"targets": {
				"to_view2": {
					"viewType": "XML",
					"transition": "slide",
					"viewName": "view2",
					"viewId": "2",
					"parent": ""
				},
				"to_view1": {
					"viewType": "XML",
					"transition": "slide",
					"viewName": "View1",
					"viewId": "1"
				}
			},
			"config": {
				"routerClass": "sap.m.routing.Router",
				"targetsClass": "sap.m.routing.Targets",
				"viewType": "XML",
				"viewPath": "new_project.view",
				"controlId": "app",
				"controlAggregation": "pages",
				"targetParent": "Page",
				"transition": "slide",
				"clearAggregation": false
			},
			"routes": [{
				"name": "to_view1",
				"pattern": "view1/{idresult}",
				"greedy": true,
				"target": ["to_view1"]
			}, {
				"name": "to_view2",
				"pattern": "home/{idtranzaction}",
				"greedy": false,
				"target": ["to_view2"]
			}]
		}

