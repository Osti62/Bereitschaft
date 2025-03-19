# Bereitschaft
<script type="text/javascript">
    document.addEventListener("DOMContentLoaded", loadData);

    function updateAllValues(selectElement) {
        const selectedValue = selectElement.value;
        document.querySelectorAll('.rowDropdown').forEach(dropdown => {
            dropdown.value = selectedValue;
        });
        saveData();
    }

    function saveData() {
        const dropdownValues = [];
        document.querySelectorAll('.rowDropdown').forEach(dropdown => {
            dropdownValues.push(dropdown.value);
        });
        localStorage.setItem('dropdownData', JSON.stringify(dropdownValues));
    }

    function loadData() {
        const savedData = localStorage.getItem('dropdownData');
        if (savedData) {
            const dropdownValues = JSON.parse(savedData);
            document.querySelectorAll('.rowDropdown').forEach((dropdown, index) => {
                if (dropdownValues[index]) {
                    dropdown.value = dropdownValues[index];
                }
            });
        }
    }
</script>

<style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 10px;
        box-sizing: border-box;
    }
    table {
        width: 100%;
        border-collapse: collapse;
    }
    th, td {
        border: 1px solid #ddd;
        padding: 12px;
        text-align: left;
    }
    th {
        background-color: #f4f4f4;
    }
    select {
        width: 100%;
        padding: 8px;
        font-size: 16px;
    }
</style>

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Kategorie
                <!-- Deaktivierte Auswahl in der Überschrift -->
                <select id="topDropdown" onchange="updateAllValues(this)" disabled>
                    <option value="Kategorie A">Kategorie A</option>
                    <option value="Kategorie B">Kategorie B</option>
                    <option value="Kategorie C">Kategorie C</option>
                </select>
            </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Produkt 1</td>
            <td>
                <select class="rowDropdown" onchange="saveData()">
                    <option value="Kategorie A">Kategorie A</option>
                    <option value="Kategorie B">Kategorie B</option>
                    <option value="Kategorie C">Kategorie C</option>
                </select>
            </td>
        </tr>
        <tr>
            <td>Produkt 2</td>
            <td>
                <select class="rowDropdown" onchange="saveData()">
                    <option value="Kategorie A">Kategorie A</option>
                    <option value="Kategorie B">Kategorie B</option>
                    <option value="Kategorie C">Kategorie C</option>
                </select>
            </td>
        </tr>
    </tbody>
</table>
