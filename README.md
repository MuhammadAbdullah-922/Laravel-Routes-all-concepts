# Laravel-Routes-all-concepts



<?php
use Illuminate\Support\Facades\Route;
Route::get('/', function () {
    return view('welcome');
})->name('home');

/*Routing with Multiparameters and methods
Route::get('/about/{id?}/comment/{comment_id?}', function( string $id=null , string $comment_id=null){
    if($id){
        return "<h1>POST ID :".$id. "</h1> <h1> Comment ID".$comment_id."</h1>";
    }
    else{
        return "No ID found";
    }
})->whereAlphanumeric('id');
*/

/*
Route::get('/about/{id?}/comment/{comment_id?}', function( string $id=null , string $comment_id=null){
    if($id){
        return "<h1>POST ID :".$id. "</h1> <h1> Comment ID".$comment_id."</h1>";
    }
    else{
        return "No ID found";
    }
})->whereIN('id',['Naat','Kallam','Manqabat']);
*/


/*
Route::get('/about/{id?}/comment/{comment_id?}', function( string $id=null , string $comment_id=null){
    if($id){
        return "<h1>POST ID :".$id. "</h1> <h1> Comment ID".$comment_id."</h1>";
    }
    else{
        return "No ID found";
    }
})->where('id','[0-9]+');
*/



/*
Route::get('/about/{id?}/comment/{comment_id?}', function( string $id=null , string $comment_id=null){
    if($id){
        return "<h1>POST ID :".$id. "</h1> <h1> Comment ID".$comment_id."</h1>";
    }
    else{
        return "No ID found";
    }
})->where('id','[a-zA-Z]+')
->whereNumber('comment_id');
*/
/*
Route::get('/about/{id?}', function( string $id=null){
    if($id){
        return "<h1>POST ID :".$id. "</h1>";
    }
    else{
        return "No ID found";
    }
});
*/

/*Route name and route groups*/

Route::get('/about_us',function(){

return view("post");

})->name ('about');

Route::get('/blog',function(){
    return view('post');
});
Route::redirect('/about_us','/blog',301);


Route::prefix('page')-> group (function(){

Route::get('/blog',function(){
    return view('welcome');
});
Route::get('/post',function(){
    return view('welcome');
});



});

route::fallback(function(){
    return"<h1>The page not found error</h1>";

});
