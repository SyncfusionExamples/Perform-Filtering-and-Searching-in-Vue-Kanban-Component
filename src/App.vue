<template>
    <div>
        <div class="componentStyles">Priority
            <ejs-dropdownlist id='priority_filter' :dataSource='priorityData' :select='prioritySelect' value='None'
                placeholder='Select a priority'>
            </ejs-dropdownlist>
        </div>
        <div class="componentStyles"> Search
            <ejs-textbox id="search_text" placeholder="Enter search text" showClearButton=true></ejs-textbox>
        </div>
    </div>
    <div class="kanban-container">
        <ejs-kanban id="kanban" ref='KanbanObj' keyField="Status" :dataSource="data" :cardSettings="cardSettings"
            :swimlaneSettings="swimlaneSettings">
            <e-columns>
                <e-column headerText="Open" keyField="Open"></e-column>
                <e-column headerText="In Progress" keyField="InProgress"></e-column>
                <e-column headerText="In Review" keyField="Review"></e-column>
                <e-column headerText="Completed" keyField="Close"></e-column>
            </e-columns>
        </ejs-kanban>
    </div>
</template>
<script>

import { KanbanComponent, ColumnsDirective, ColumnDirective } from "@syncfusion/ej2-vue-kanban";
import { DropDownListComponent } from "@syncfusion/ej2-vue-dropdowns";
import { Query } from "@syncfusion/ej2-data";
import { TextBoxComponent } from "@syncfusion/ej2-vue-inputs";
export default {
    components: {
        "ejs-kanban": KanbanComponent,
        "e-columns": ColumnsDirective,
        "e-column": ColumnDirective,
        'ejs-dropdownlist': DropDownListComponent,
        'ejs-textbox': TextBoxComponent
    },
    data: function () {
        return {
            data: [
                {
                    "Id": "Task 1",
                    "Title": "Task - 29001",
                    "Status": "Open",
                    "Summary": "Analyze the new requirements gathered from the customer.",
                    "Type": "Story",
                    "Priority": "Low",
                    "Tags": "Analyze,Customer",
                    "Estimate": 3.5,
                    "Assignee": "Nancy Davloio",
                    "RankId": 1,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-low, e-nancy-davloio"
                },
                {
                    "Id": "Task 2",
                    "Title": "Task - 29002",
                    "Status": "InProgress",
                    "Summary": "Improve application performance",
                    "Type": "Improvement",
                    "Priority": "Normal",
                    "Tags": "Improvement",
                    "Estimate": 6,
                    "Assignee": "Andrew Fuller",
                    "RankId": 1,
                    "Color": "#673AB8",
                    "ClassName": "e-improvement, e-normal, e-andrew-fuller"
                },
                {
                    "Id": "Task 3",
                    "Title": "Task - 29003",
                    "Status": "Open",
                    "Summary": "Arrange a web meeting with the customer to get new requirements.",
                    "Type": "Others",
                    "Priority": "Critical",
                    "Tags": "Meeting",
                    "Estimate": 5.5,
                    "Assignee": "Janet Leverling",
                    "RankId": 2,
                    "Color": "#1F88E5",
                    "ClassName": "e-others, e-critical, e-janet-leverling"
                },
                {
                    "Id": "Task 4",
                    "Title": "Task - 29004",
                    "Status": "InProgress",
                    "Summary": "Fix the issues reported in the IE browser.",
                    "Type": "Bug",
                    "Priority": "Critical",
                    "Tags": "IE",
                    "Estimate": 2.5,
                    "Assignee": "Janet Leverling",
                    "RankId": 2,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-release, e-janet-leverling"
                },
                {
                    "Id": "Task 5",
                    "Title": "Task - 29005",
                    "Status": "Review",
                    "Summary": "Fix the issues reported by the customer.",
                    "Type": "Bug",
                    "Priority": "Low",
                    "Tags": "Customer",
                    "Estimate": "3.5",
                    "Assignee": "Steven walker",
                    "RankId": 1,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-low, e-steven-walker"
                },
                {
                    "Id": "Task 6",
                    "Title": "Task - 29007",
                    "Status": "Validate",
                    "Summary": "Validate new requirements",
                    "Type": "Improvement",
                    "Priority": "Low",
                    "Tags": "Validation",
                    "Estimate": 1.5,
                    "Assignee": "Robert King",
                    "RankId": 1,
                    "Color": "#673AB8",
                    "ClassName": "e-improvement, e-low, e-robert-king"
                },
                {
                    "Id": "Task 7",
                    "Title": "Task - 29009",
                    "Status": "Review",
                    "Summary": "Fix the issues reported in Safari browser.",
                    "Type": "Bug",
                    "Priority": "Critical",
                    "Tags": "Fix,Safari",
                    "Estimate": 1.5,
                    "Assignee": "Nancy Davloio",
                    "RankId": 2,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-release, e-nancy-davloio"
                },
                {
                    "Id": "Task 8",
                    "Title": "Task - 29010",
                    "Status": "Close",
                    "Summary": "Test the application in the IE browser.",
                    "Type": "Story",
                    "Priority": "Low",
                    "Tags": "Review,IE",
                    "Estimate": 5.5,
                    "Assignee": "Margaret hamilt",
                    "RankId": 3,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-low, e-margaret-hamilt"
                },
                {
                    "Id": "Task 9",
                    "Title": "Task - 29011",
                    "Status": "Validate",
                    "Summary": "Validate the issues reported by the customer.",
                    "Type": "Story",
                    "Priority": "High",
                    "Tags": "Validation,Fix",
                    "Estimate": 1,
                    "Assignee": "Steven walker",
                    "RankId": 1,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-high, e-steven-walker"
                },
                {
                    "Id": "Task 10",
                    "Title": "Task - 29015",
                    "Status": "Open",
                    "Summary": "Show the retrieved data from the server in grid control.",
                    "Type": "Story",
                    "Priority": "High",
                    "Tags": "Database,SQL",
                    "Estimate": 5.5,
                    "Assignee": "Margaret hamilt",
                    "RankId": 4,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-high, e-margaret-hamilt"
                },
                {
                    "Id": "Task 11",
                    "Title": "Task - 29016",
                    "Status": "InProgress",
                    "Summary": "Fix cannot open user’s default database SQL error.",
                    "Priority": "Critical",
                    "Type": "Bug",
                    "Tags": "Database,Sql2008",
                    "Estimate": 2.5,
                    "Assignee": "Janet Leverling",
                    "RankId": 4,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-critical, e-janet-leverling"
                },
                {
                    "Id": "Task 12",
                    "Title": "Task - 29017",
                    "Status": "Review",
                    "Summary": "Fix the issues reported in data binding.",
                    "Type": "Story",
                    "Priority": "Normal",
                    "Tags": "Databinding",
                    "Estimate": "3.5",
                    "Assignee": "Janet Leverling",
                    "RankId": 4,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-normal, e-janet-leverling"
                },
                {
                    "Id": "Task 13",
                    "Title": "Task - 29018",
                    "Status": "Close",
                    "Summary": "Analyze SQL server 2008 connection.",
                    "Type": "Story",
                    "Priority": "Critical",
                    "Tags": "Grid,Sql",
                    "Estimate": 2,
                    "Assignee": "Andrew Fuller",
                    "RankId": 4,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-release, e-andrew-fuller"
                },
                {
                    "Id": "Task 14",
                    "Title": "Task - 29019",
                    "Status": "Validate",
                    "Summary": "Validate databinding issues.",
                    "Type": "Story",
                    "Priority": "Low",
                    "Tags": "Validation",
                    "Estimate": 1.5,
                    "Assignee": "Margaret hamilt",
                    "RankId": 1,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-low, e-margaret-hamilt"
                },
                {
                    "Id": "Task 15",
                    "Title": "Task - 29020",
                    "Status": "Close",
                    "Summary": "Analyze grid control.",
                    "Type": "Story",
                    "Priority": "High",
                    "Tags": "Analyze",
                    "Estimate": 2.5,
                    "Assignee": "Margaret hamilt",
                    "RankId": 5,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-high, e-margaret-hamilt"
                },
                {
                    "Id": "Task 16",
                    "Title": "Task - 29021",
                    "Status": "Close",
                    "Summary": "Stored procedure for initial data binding of the grid.",
                    "Type": "Others",
                    "Priority": "Critical",
                    "Tags": "Databinding",
                    "Estimate": 1.5,
                    "Assignee": "Steven walker",
                    "RankId": 6,
                    "Color": "#1F88E5",
                    "ClassName": "e-others, e-release, e-steven-walker"
                },
                {
                    "Id": "Task 17",
                    "Title": "Task - 29022",
                    "Status": "Close",
                    "Summary": "Analyze stored procedures.",
                    "Type": "Story",
                    "Priority": "Critical",
                    "Tags": "Procedures",
                    "Estimate": 5.5,
                    "Assignee": "Janet Leverling",
                    "RankId": 7,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-release, e-janet-leverling"
                },
                {
                    "Id": "Task 18",
                    "Title": "Task - 29023",
                    "Status": "Validate",
                    "Summary": "Validate editing issues.",
                    "Type": "Story",
                    "Priority": "Critical",
                    "Tags": "Editing",
                    "Estimate": 1,
                    "Assignee": "Nancy Davloio",
                    "RankId": 1,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-critical, e-nancy-davloio"
                },
                {
                    "Id": "Task 19",
                    "Title": "Task - 29024",
                    "Status": "Review",
                    "Summary": "Test editing functionality.",
                    "Type": "Story",
                    "Priority": "Normal",
                    "Tags": "Editing,Test",
                    "Estimate": 0.5,
                    "Assignee": "Nancy Davloio",
                    "RankId": 5,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-normal, e-nancy-davloio"
                },
                {
                    "Id": "Task 20",
                    "Title": "Task - 29025",
                    "Status": "Open",
                    "Summary": "Enhance editing functionality.",
                    "Type": "Improvement",
                    "Priority": "Low",
                    "Tags": "Editing",
                    "Estimate": 3.5,
                    "Assignee": "Andrew Fuller",
                    "RankId": 5,
                    "Color": "#673AB8",
                    "ClassName": "e-improvement, e-low, e-andrew-fuller"
                },
                {
                    "Id": "Task 21",
                    "Title": "Task - 29026",
                    "Status": "InProgress",
                    "Summary": "Improve the performance of the editing functionality.",
                    "Type": "Epic",
                    "Priority": "High",
                    "Tags": "Performance",
                    "Estimate": 6,
                    "Assignee": "Nancy Davloio",
                    "RankId": 5,
                    "Color": "#e91e64",
                    "ClassName": "e-epic, e-high, e-nancy-davloio"
                },
                {
                    "Id": "Task 22",
                    "Title": "Task - 29027",
                    "Status": "Open",
                    "Summary": "Arrange web meeting with the customer to show editing demo.",
                    "Type": "Others",
                    "Priority": "High",
                    "Tags": "Meeting,Editing",
                    "Estimate": 5.5,
                    "Assignee": "Steven walker",
                    "RankId": 6,
                    "Color": "#1F88E5",
                    "ClassName": "e-others, e-high, e-steven-walker"
                },
                {
                    "Id": "Task 23",
                    "Title": "Task - 29029",
                    "Status": "Review",
                    "Summary": "Fix the editing issues reported by the customer.",
                    "Type": "Bug",
                    "Priority": "Low",
                    "Tags": "Editing,Fix",
                    "Estimate": "3.5",
                    "Assignee": "Janet Leverling",
                    "RankId": 6,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-low, e-janet-leverling"
                },
                {
                    "Id": "Task 24",
                    "Title": "Task - 29030",
                    "Status": "Testing",
                    "Summary": "Fix the issues reported by the customer.",
                    "Type": "Bug",
                    "Priority": "Critical",
                    "Tags": "Customer",
                    "Estimate": "3.5",
                    "Assignee": "Steven walker",
                    "RankId": 1,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-critical, e-steven-walker"
                },
                {
                    "Id": "Task 25",
                    "Title": "Task - 29031",
                    "Status": "Testing",
                    "Summary": "Fix the issues reported in Safari browser.",
                    "Type": "Bug",
                    "Priority": "Critical",
                    "Tags": "Fix,Safari",
                    "Estimate": 1.5,
                    "Assignee": "Nancy Davloio",
                    "RankId": 2,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-release, e-nancy-davloio"
                },
                {
                    "Id": "Task 26",
                    "Title": "Task - 29032",
                    "Status": "Testing",
                    "Summary": "Check Login page validation.",
                    "Type": "Story",
                    "Priority": "Critical",
                    "Tags": "Testing",
                    "Estimate": 0.5,
                    "Assignee": "Michael Suyama",
                    "RankId": 3,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-release, e-michael-suyama"
                },
                {
                    "Id": "Task 27",
                    "Title": "Task - 29033",
                    "Status": "Testing",
                    "Summary": "Fix the issues reported in data binding.",
                    "Type": "Story",
                    "Priority": "Normal",
                    "Tags": "Databinding",
                    "Estimate": "3.5",
                    "Assignee": "Janet Leverling",
                    "RankId": 4,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-normal, e-janet-leverling"
                },
                {
                    "Id": "Task 28",
                    "Title": "Task - 29034",
                    "Status": "Testing",
                    "Summary": "Test editing functionality.",
                    "Type": "Story",
                    "Priority": "Normal",
                    "Tags": "Editing,Test",
                    "Estimate": 0.5,
                    "Assignee": "Nancy Davloio",
                    "RankId": 5,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-normal, e-nancy-davloio"
                },
                {
                    "Id": "Task 29",
                    "Title": "Task - 29035",
                    "Status": "Testing",
                    "Summary": "Fix editing issues reported in Firefox.",
                    "Type": "Bug",
                    "Priority": "Critical",
                    "Tags": "Editing,Fix",
                    "Estimate": 1.5,
                    "Assignee": "Robert King",
                    "RankId": 7,
                    "Color": "#E64A19",
                    "ClassName": "e-bug, e-critical, e-robert-king"
                },
                {
                    "Id": "Task 30",
                    "Title": "Task - 29036",
                    "Status": "Testing",
                    "Summary": "Test editing feature in the IE browser.",
                    "Type": "Story",
                    "Priority": "Normal",
                    "Tags": "Testing",
                    "Estimate": 5.5,
                    "Assignee": "Janet Leverling",
                    "RankId": 10,
                    "Color": "#02897B",
                    "ClassName": "e-story, e-normal, e-janet-leverling"
                }
            ],
            cardSettings: {
                contentField: "Summary",
                headerField: "Id",
            },
            swimlaneSettings: {
                keyField: "Assignee"
            },
            priorityData: ["None", "High", "Normal", "Low"]
        }
    },
    mounted: function () {
        this.kanbanObj = this.$refs.KanbanObj.ej2Instances;

        document.getElementById('search_text').addEventListener('keyup', (e) => {
            let searchValue = e.target.value;
            let searchQuery = new Query();
            if (searchValue !== '') {
                searchQuery = new Query().search(searchValue, ['Id', 'Summary'], 'contains', true);
            }
            this.kanbanObj.query = searchQuery;
        });
    },
    methods: {
        prioritySelect: function (args) {
            let filterQuery = new Query();
            if (args.itemData.value !== 'None') {
                filterQuery = new Query().where('Priority', 'equal', args.itemData.value);
            }
            this.kanbanObj.query = filterQuery;
        }
    }
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';

.componentStyles {
    width: 120px;
    text-align: left;
    font-weight: bold;
    padding: 8px 0 8px 10px;
}

.kanban-container {
    min-height: 350px;
    height: 550px;
    width: 100%;
    overflow-y: auto;
    padding-top: 8px;
}
</style>