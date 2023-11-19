<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Cookie;

class ProfileController extends Controller
{
    public function index(Request $request, $id){
        $id = $request->id;
        $name = "Donal Trump";
        $age = "75";

        $data = [
            'id' => $id,
            'name' => $name,
            'age' => $age,
        ];

        // Set the cookie parameters
        $name = 'access_token';
        $value = '123-XYZ';
        $minutes = 1;
        $path = '/';
        $domain = $_SERVER['SERVER_NAME'];
        $secure = false;
        $httpOnly = true;

        $cookie = Cookie::make($name, $value, $minutes, $path, $domain, $secure, $httpOnly);
        $response = response($data, 200)->cookie($cookie);
        return $response;
    }
}
