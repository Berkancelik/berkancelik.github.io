<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Converter</title>
  
    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  
    <!-- Bootstrap Icons -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons%401.5.0/font/bootstrap-icons.css">

</head>
<body>

    <div class="container mt-5">
     <div class="row">
    <div class="col-md-4 form-group">
        <textarea class="form-control" rows="10" id="inputTextArea" onclick="resetText()" oninput="convertText()"></textarea>
    </div>
    <div class="col-md-4 form-group">
        <select class="form-control" id="conversionType" onchange="resetText();convertText()">
            <option value="textToBinary">Text to Binary</option>
            <option value="binaryToText">Binary to Text</option>
        </select>
    </div>
    <div class="col-md-4 form-group">
        <textarea class="form-control" rows="10" id="outputTextArea" readonly></textarea>
    </div>
</div>

        <div class="row mt-3 text-center">
            <div class="col-md-12">
                <button type="button" class="btn btn-secondary" onclick="copyText()">  <i class="bi bi-clipboard"></i> <span class="ms-2">Kopyala</span></button>
                <button type="button" class="btn btn-danger" onclick="resetText()"> <i class="bi bi-arrow-counterclockwise"></i> <span class="ms-2">Sıfırla</span></button>
                <button type="button" class="btn btn-info" onclick="shareOnTwitter()">  <i class="bi bi-twitter"></i> <span class="ms-2">Twitter'da Paylaş</span></button>

            </div>
        </div>
    </div>

    <!-- Bootstrap JS -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

        <script>
            function convertText() {
                var inputTextArea = document.getElementById("inputTextArea");
                var outputTextArea = document.getElementById("outputTextArea");
                var conversionType = document.getElementById("conversionType").value;
                if (conversionType === "textToBinary") {
                    outputTextArea.value = textToBinary(inputTextArea.value);
                } else if (conversionType === "binaryToText") {
                    outputTextArea.value = binaryToText(inputTextArea.value);
                }
            }

            function textToBinary(text) {
                return text.split('').map(function (char) {
                    return char.charCodeAt(0).toString(2).padStart(8, '0');
                }).join(' ');
            }

            function binaryToText(binary) {
                return binary.split(' ').map(function (bin) {
                    return String.fromCharCode(parseInt(bin, 2));
                }).join('');
            }

            function copyText() {
            var outputTextArea = document.getElementById("outputTextArea");
            outputTextArea.select();
            document.execCommand("copy");
        }
        function shareOnTwitter() {
            var outputTextArea = document.getElementById("outputTextArea");
            var tweetText = encodeURIComponent(outputTextArea.value);
            window.open("https://twitter.com/intent/tweet?text=" + tweetText);
        }
        function resetText() {
            document.getElementById("inputTextArea").value = "";
            document.getElementById("outputTextArea").value = "";
        }
    </script>

