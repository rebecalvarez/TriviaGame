var countStartNumber = 30;

var triviaGame = {
 questions : [
 {
    question: "Which of the following items was owned by the fewest U.S. homes in 1990?",
    choices:["Home Computer","Compact Disk Player","Cordless Phone", "Dishwasher"],
    answer:"Compact Disk Player",
    pic: "assets/images/disk.gif"
},

 {
    question: "What was the first game controller with vibration feedback?",
    choices:["Sega Dreamcast Controller","Nintendo 64 controller","Nintendo GameCube controller","Sony DualShock controller"],
    answer:"Nintendo 64 controller",
    pic: "assets/images/nt64.gif"
},

 {
    question: "Which telephone giant has a trademark on the term ‘flip phone’",
    choices:["iPhone","Nokia","Motorola","Erikson"],
    answer:"Motorola",
    pic: "assets/images/flip.gif"
},

 {
    question: "Who gave the name ‘Computer Virus’?",
    choices:["Bill Gates","Steve Jobs","Dr. Fred Cohen.","Richard Branson"],
    answer:"Dr. Fred Cohen.",
    pic: "assets/images/cohen.jpg"
},

{
    question: "Which globally famous job-search portal’s trademarked tagline is `never settle’?",
    choices:["Monster.com","Indeed","The ladders","Glassdoor"],
    answer:"Monster.com",
    pic: "assets/images/monster.gif"
},

{
    question: "Which famous PC company is headquartered at Round Rock, Texas?",
    choices:["Lenovo","Microsoft","Dell","Acer"],
    answer:"Dell",
    pic: "assets/images/dell.gif"
},

{
    question: " Who claims to be the ‘First Internet search engine to launch Image, Audio, and Video search capabilities’?",
    choices:["Google","Bing","Yahoo","Alta Vista"],
    answer:"Alta Vista",
    pic: "assets/images/altavista.jpg"
},

{
    question: "Who quoted “I Would Trade all my technology for an afternoon with Socrates”",
    choices:["Elon Musk","Steve Jobs","Bill Gates","Mark Zuckerberg"],
    answer:"Steve Jobs",
    pic: "assets/images/stevejobs.gif"
},
 {
    question: "What is sometimes described as the “SMS of the internet?”",
    choices:["Twitter","Facebook","Instagram", "Snap Chat"],
    answer:"Twitter",
    pic: "assets/images/twitter.gif"
},

{
    question: "Who created the first personal computer?",
    choices:["IBM","Ed Roberts","Texas Instruments","Acer"],
    answer:"Ed Roberts",
    pic: "assets/images/ed.jpg"
},
{
    question: "What is the world's best-selling PC game?",
    choices:["World of Warcraft","Half-Life 2","Minecraft","Doom"],
    answer:"Minecraft",
    pic: "assets/images/minecraft.gif"
}
]
,
currentQuestion: 0
,
counter: countStartNumber
,
correct:0
,
incorrect:0
,
countdown: function() {
    triviaGame.counter--;
    $("#timer").html(triviaGame.counter);
    if ( triviaGame.counter === 0){
        triviaGame.timeUp();
    }
}
,
loadQuestion: function(){
    timer= setInterval(this.countdown, 1000);
   console.log(this.currentQuestion, "this is current question" );
    $("#question").html(this.questions[this.currentQuestion].question);

         $('#ch-1').html('<button   class="btn btn-outline-info" data-name="' 
          + this.questions[this.currentQuestion].choices[0] + '">' 
          + this.questions[this.currentQuestion].choices[0] + '</button>');
          $('#ch-2').html('<button class="btn btn-outline-info" data-name="' 
          + this.questions[this.currentQuestion].choices[1] + '">' 
          + this.questions[this.currentQuestion].choices[1] + '</button>');
          $('#ch-3').html('<button class="btn btn-outline-info" data-name="' 
          + this.questions[this.currentQuestion].choices[2] + '">' 
          + this.questions[this.currentQuestion].choices[2] + '</button>');
          $('#ch-4').html('<button class="btn btn-outline-info" data-name="' 
          + this.questions[this.currentQuestion].choices[3] + '">' 
          + this.questions[this.currentQuestion].choices[3] + '</button>');     
  
}
,
nextQuestion: function() {
    $("#correctAnswer").hide();
    $(".answers").show();
    $("#gamecontent").show();
    $(".results").hide();
    triviaGame.counter = countStartNumber;
    $("#timer").html(triviaGame.counter);
    triviaGame.currentQuestion++;
    triviaGame.loadQuestion();
    console.log("we are in NextQuestion");
}
,
timeUp: function(){
    
    clearInterval(timer);
    triviaGame.wrongaudio.play();
    $("#timer").html(this.counter);
    $("#gamecontent").hide();
    $("#correctAnswer").show();
    $("#correctAnswer").html('<h2>Out of Time!</h2>' + '<br> <h3>The Answer is :' + this.questions[this.currentQuestion].answer + 
    '</h3> <br> <img class="c-image" src="' + this.questions[this.currentQuestion].pic + '" />');
   
    if (this.currentQuestion === this.questions.length - 1) {
        setTimeout(this.results, 3000);
    } else {
        setTimeout(this.nextQuestion, 3000);
    }
}
,
results : function (){
    clearInterval(timer);
    $('#gamecontent').hide();
    $(".results").show();
    $("#correctAnswer").hide();
    $('#title').hide()
   

    if (triviaGame.correct >= 5){
        triviaGame.winneraudio.play();
        $('.results').html('<h3>Correct answers: ' + triviaGame.correct +
        '</h3> <br> <h3>Wrong Answers: ' + triviaGame.incorrect +
        '<h2><br>All Systems back Online! You made it!</h2> <br>' +
         '<img class="recording"src="assets/images/youwon.gif"/> <br>'+ 
        '</h3><br><button class="btn btn-info start text-center" id="btn-start">Start Over?</button>')

    }else{
        triviaGame.loseraudio.play();
        $('.results').html('<h3>Correct answers: ' + triviaGame.correct +
        '</h3> <br> <h3>Wrong Answers: ' + triviaGame.incorrect + '<h2> <br>Systems Down, Abandon the Ship NOW!</h2> <br>' +
         '<img class="recording"src="assets/images/lost.gif"/> <br>'+
        
        '</h3> <br><button class="btn btn-info start text-center" id="btn-start">Start Over?</button>')

    }



     $(document).on('click','#btn-start', function() {
        $('#gamecontent').show(); 
         $(".results").hide();
    
    });
}

,
clicked: function(e) {
    clearInterval(timer);
    if($(e.target).data('name') === this.questions[this.currentQuestion].answer){
        console.log($(e.target));
        this.answerCorrectly();
    } else {this.answerIncorrectly();
    }
}
,
answerCorrectly: function(){
    clearInterval(timer);
    triviaGame.rightaudio.play();
    this.correct++;
    console.log(this.correct);
    $("#gamecontent").hide();
    $(".results").show();
    $(".results").html('<img class="text-center"src="assets/images/check.png"/> <br>' + '<br> <img class="c-image" src="' + this.questions[this.currentQuestion].pic + '" />');

    if (this.currentQuestion === this.questions.length - 1){
        setTimeout(this.results, 3 * 1000);
    } else {
        setTimeout(triviaGame.nextQuestion, 3 * 1000);
        
    }
    
}
,
answerIncorrectly: function(){
    clearInterval(timer);
    triviaGame.wrongaudio.play();
    this.incorrect++;
    $("#gamecontent").hide();
    $(".results").show();
    $(".results").html('<img class="text-center"src="assets/images/wrong.png"/> <br>'+'<br><h3>Right Answer: ' + this.questions[this.currentQuestion].answer +'</h3>'
    +'<img class="c-image" src="' + this.questions[this.currentQuestion].pic + '" />');
    if (this.currentQuestion === this.questions.length - 1){
        console.log(this.currentQuestion);
        setTimeout(this.results, 3 * 1000);
    }else {
        
        setTimeout(triviaGame.nextQuestion, 3 * 1000);
    }

}
,

playGame : function(){
    $('#title').show();
    this.currentQuestion = 0;
    this.counter = countStartNumber;
    this.correct = 0;
    this.incorrect = 0;
    this.loadQuestion();
}
,
entranceaudio : new Audio("./assets/audio/entrance.wav")
,
rightaudio : new Audio("./assets/audio/right.wav")
,
wrongaudio : new Audio("./assets/audio/wrong.wav")
,
winneraudio : new Audio("./assets/audio/winner.wav")
,
loseraudio : new Audio("./assets/audio/sorry_dave.wav")
}



/////////////  END OF OBJECT  ///////////////////////////////////////////////

///////////////////////////////////////////////////////////////////////////

$(document).on('click', '.answer-button', function(e) {
    triviaGame.clicked(e);
  });

$(document).on('click','#btn-start', function() {
    console.log(this);
    $('#myModal').hide();
    triviaGame.playGame();
});

$(document).ready(function() {
    $("#my_audio").get(0).play();
});

