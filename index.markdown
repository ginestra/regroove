---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<!-- rendering area -->
<div id="sheetMusicDiv" class="fullWidthEle">
    <div id="svgTarget" class="svgTarget">
        <!-- space for the SVG sheet music to display -->
    </div>
</div>
<p class="warnings">Warnings:</p>
<div class="warnings" id="diverr">
</div>
<div id="sheetMusicTextFields" class="fullWidthEle grooveDB_hidden edit-block">
    <span class="sheetMusicTextField"><b>Title:</b> <input class="sheetMusicInputField" id="tuneTitle" onchange="myGrooveWriter.refresh_ABC();" type="text"></span>
    <span class="sheetMusicTextField"><b>Author:</b> <input class="sheetMusicInputField" id="tuneAuthor" onchange="myGrooveWriter.refresh_ABC();"  type="text"></span>
    <span class="sheetMusicTextField"><b>Comment:</b> <input class="sheetMusicInputField" id="tuneComments" onchange="myGrooveWriter.refresh_ABC();"  type="text"></span>
    <span id='KeyButton'><input type="checkbox" class="hiddenCheckbox" id="showLegend" onclick="myGrooveWriter.refresh_ABC();"><label id="LegendLabel" for="showLegend"><i class="fa fa-key"></i></label></span>
</div>
<!-- This block is where the music can be edited -->
<div id="musicalInput" class="fullWidthEle edit-block">
    <div id="measureContainer">
        <script type="text/javascript">
            var genHTML = "";
            var cur_measure;
            for (cur_measure = 1; cur_measure <= myGrooveWriter.numberOfMeasures(); cur_measure++) {
            genHTML += myGrooveWriter.HTMLforStaffContainer(cur_measure, (cur_measure - 1) * myGrooveWriter.notesPerMeasure());
            }
            document.write(genHTML);
            //console.log(genHTML);
        </script>
    </div>
</div>

<!-- This is the block where the bottom buttons are - Note that it's using `span` instead of `button`  -->

<div id="bottomButtonRow" class="fullWidthEle">
    <span class="pageBottomButton edit-block" id="clearAllNotesButton" onclick="event.preventDefault(); myGrooveWriter.clearAllNotes();"><span class="bottomButtonIcon"><i class="fa fa-trash fa-2x"></i></span><span class="bottomButtonLabel">CLEAR ALL</span></span>
    <span class="pageBottomButton edit-block" id="showHideTomsButton" onclick="event.preventDefault(); myGrooveWriter.showHideToms(false, false);"><span class="bottomButtonIcon"><i id="icon-tom1" class="fa fa-circle"></i><i id="icon-tom2" class="fa fa-circle-o"></i><i id="icon-tom3" class="fa fa-circle-o"></i></span><span class="bottomButtonLabel">TOMS</span></span>
    <span class=" grooveDB_hidden pageBottomButton" id="stickingsButton" onclick="myGrooveWriter.stickingsAnchorClick();"><span class="bottomButtonLabel">STICKINGS</span></span>
    <span class=" grooveDB_hidden pageBottomButton" id="downloadButton" onclick="myGrooveWriter.DownloadAnchorClick();"><span class="bottomButtonIcon"><i class="fa fa-download fa-2x"></i></span><span class="bottomButtonLabel">DOWNLOAD</span></span>
    <span class=" grooveDB_hidden pageBottomButton" id="printButton" onclick="myGrooveWriter.printMusic();"><span class="bottomButtonIcon"><i class="fa fa-print fa-2x"></i></span><span class="bottomButtonLabel">PRINT</span></span>
    <span class=" grooveDB_hidden pageBottomButton" id="shareSaveButton" onclick="event.preventDefault(); myGrooveWriter.show_FullURLPopup();"><span class="bottomButtonIcon"><i class="fa fa-share fa-2x"></i></span><span class="bottomButtonLabel">SHARE</span></span>
</div>