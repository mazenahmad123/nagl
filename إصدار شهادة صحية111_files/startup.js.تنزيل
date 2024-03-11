var arabicDataTableOptions = {
    search: "",
    searchPlaceholder: "بحث ...",
    info: "_TOTAL_ سجل",
    emptyTable: "عزيزي المستفيد... لا توجد سجلات",
    infoEmpty: "",
    infoFiltered: "",
    loadingRecords: "تحميل ...",
    lengthMenu: "عرض _MENU_ سجل",
    zeroRecords: "عزيزي المستفيد... لا توجد سجلات",
    paginate: {
        first: 'الاول',
        previous: 'السابق',
        next: 'التالي',
        last: 'الاخير'
    },
    select: {
        rows: " / السجلات المحددة %d "
    }
};
var defultDom = "<'row'<'col-sm-12'f>><'row'<'col-sm-12'tr>><'row'<'col-sm-4 center'il><'col-sm-8'p>>";
var noSearchDom = "<'row'<'col-sm-12'tr>><'row'<'col-sm-4 center'il><'col-sm-8'p>>";

var datatable_lengthMenu = [[5, 10, 15, 20, 25, 50, 75, 100], [5, 10, 15, 20, 25, 50, 75, 100]];

function loadlist(select, url, data, valueKey, textKey, addEmpty = false, emptyValue = null, emptyText = null, dataKeys = null, selectedValue = null, callback = null, fail = null) {
   
    $(select).empty();
    if (addEmpty) {
        var emptyOption = $("<option value=''></option>");
        if (emptyValue)
            emptyOption.val(emptyValue);
        if (emptyText)
            emptyOption.html(emptyText);
        $(select).append(emptyOption);
    }
    $.getJSON(url, data, function (data) {
        
        if (data && data.length > 0)
            $.each(data, function (i, obj) {
                var option;
                if (selectedValue && obj[valueKey] == selectedValue)
                    option = $('<option selected>');
                else
                    option = $('<option>');
                option.val(obj[valueKey]).text(obj[textKey]);
                if (dataKeys && dataKeys.length > 0)
                    $.each(dataKeys, function (index, dataKey) {
                        $(option).data(dataKey, obj[dataKey]);
                    });
                $(select).append(option);
            });
        if (callback)
            callback(data);

    }).fail(function () {
        if (fail)
            fail();
    });
}
function loadlistWithMultiTextKey(select, url, data, valueKey, textKeys, addEmpty = false, emptyValue = null, emptyText = null, dataKeys = null, selectedValue = null, callback = null, fail = null) {

    $(select).empty();
    if (addEmpty) {
        var emptyOption = $("<option value=''></option>");
        if (emptyValue)
            emptyOption.val(emptyValue);
        if (emptyText)
            emptyOption.html(emptyText);
        $(select).append(emptyOption);
    }
    $.getJSON(url, data, function (data) {

        if (data && data.length > 0)
            $.each(data, function (i, obj) {
                var option;
                if (selectedValue && obj[valueKey] == selectedValue)
                    option = $('<option selected>');
                else
                    option = $('<option>');
                var text = '';
                $.each(textKeys, function (j, textKey) {
                    if (j == 0)
                        text += obj[textKey];
                    else
                        text += ', ' + obj[textKey];
                });
                option.val(obj[valueKey]).text(text);
                if (dataKeys && dataKeys.length > 0)
                    $.each(dataKeys, function (index, dataKey) {
                        $(option).data(dataKey, obj[dataKey]);
                    });
                $(select).append(option);
            });
        if (callback)
            callback();

    }).fail(function () {
        if (fail)
            fail();
    });
}
function loadlistStatic(select, array, valueKey, textKey, addEmpty, emptyValue, emptyText, dataKeys, selectedValue, callback) {
    $(select).empty();
    if (addEmpty) {
        var emptyOption = $("<option value=''></option>");
        //if (emptyValue)
            emptyOption.val(emptyValue);
        if (emptyText)
            emptyOption.html(emptyText);
        $(select).append(emptyOption);
    }
    if (array && array.length > 0) {
        $.each(array, function (i, obj) {
            var option;
            if (valueKey && textKey) {
                if (selectedValue && obj[valueKey] == selectedValue)
                    option = $('<option selected>');
                else
                    option = $('<option>');
                option.val(obj[valueKey]).text(obj[textKey]);
                if (dataKeys && dataKeys.length > 0)
                    $.each(dataKeys, function (index, dataKey) {
                        $(option).data(dataKey, obj[dataKey]);
                    });
            }
            else {
                if (selectedValue && obj == selectedValue)
                    option = $('<option selected>');
                else
                    option = $('<option>');
                option.val(obj).text(obj);
            }
            $(select).append(option);
        });
        if (callback)
            callback();
    }
}
function createCalenders(calendar,minDate,maxDate) {

    var cal = $.calendars.instance('ummalqura');
    return $(calendar).calendarsPicker({
        calendar: cal,
        minDate: minDate,
        maxDate: maxDate,
        showTrigger: '#calImg',
        dateFormat: 'yyyy/mm/dd',
        onSelect: function () {
            $(this).trigger("change").parsley().reset();
        }
    });
}
function createCalendersWithRang(calendar, minDate, maxDate, calenderType, rang) {

    var cal = $.calendars.instance(calenderType);
    return $(calendar).calendarsPicker({
        calendar: cal,
        changeYear: true,
        yearRange: rang,
        minDate: minDate,
        maxDate: maxDate,
        showTrigger: '#calImg',
        dateFormat: 'yyyy/mm/dd',
        onSelect: function () {
            $(this).trigger("change").parsley().reset();
        }
    });
}