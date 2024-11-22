import Foundation

class Banco{
    var nombreBanco:String
    var direccionBanco:String
    private var idBanco:String
    
    init(){
        nombreBanco=""
        direccionBanco=""
        idBanco=""
    }
    init(nombreBanco:String,direccionBanco:String,idBanco:String){
        self.nombreBanco=nombreBanco
        self.direccionBanco=direccionBanco
        self.idBanco=idBanco
    }
    func verDatosBanco(){
        print(nombreBanco)
        print(direccionBanco)
    }
    func cambiarDatosBanco(){
        print("Cambiar nombre")
        print("Cambiar dirección")
    }
    func setidBanco(idBanco:String){
        self.idBanco=idBanco
    }
    func getidBanco()->String{
        return idBanco
    }
}
class Cliente:Banco{
    var nombreCliente:String
    var edad:Int
    private var dineroCuenta:Double
    private var password:String
    override init(){
        nombreCliente=""
        edad=0
        dineroCuenta=0.0
        password=""
        super.init()
    }
    init(nombreCliente:String,edad:Int,dineroCuenta:Double,
    password:String,nombreBanco:String,direccionBanco:String,idBanco:String){
        self.nombreCliente=nombreCliente
        self.edad=edad
        self.dineroCuenta=dineroCuenta
        self.password=password
        super.init(nombreBanco:nombreBanco,direccionBanco:direccionBanco,
        idBanco:idBanco)
    }
    init(nombreCliente: String, edad: Int, dineroCuenta: Double, password: String) {
        self.nombreCliente=nombreCliente
        self.edad=edad
        self.dineroCuenta=dineroCuenta
        self.password=password
        super.init(nombreBanco: "Banco Default", direccionBanco: "Dirección Default", idBanco: "ID Default")
    }
    func nuevoCliente(){
        print("Ingrese un nuevo cliente: ")
    }
    private func verDineroCliente(){
        print("El dinero del cliente es \(dineroCuenta)")
    }
    func verDatosCliente(){
        print(nombreBanco)
        print(edad)
    }
    private func cambiarPasswordCliente(){
        print("Cambiar contraseña")
    }
    func getCambiarPasswordCliente(){
        cambiarPasswordCliente()
    }
    func getverDineroCliente(){
        verDineroCliente()
    }
    func setDineroCuenta(dinero:Double){
        self.dineroCuenta=dinero
    }
    func getDineroCuenta()->Double{
        return dineroCuenta
    }
    func setPassword(password:String){
        self.password=password
    }
    func getPassword()->String{
        return password
    }
}
var opc=0
var array=[Cliente]()
repeat{
    print("Bienvenido al Menú de PumaBanco")
    print("1-Administrador")
    print("2-Cliente")
    print("3-Salir")
    opc=Int(readLine()!)!
    
    if(opc==1){
        var opcion=0
        repeat{
            print("Menú Administrador")
            print("1-Agragar nuevo cliente")
            print("2-Eliminar cliente")
            print("3-Ver datos del banco")
            print("4-Cambiar id del banco")
            print("5-salir")
            opcion=Int(readLine()!)!
            if(opcion==1){
                print("Ingrese el nombre del nuevo cliente: ")
                var nombre=readLine()!
                if array.contains(where:{$0.nombreCliente == nombre }){
                print("\(nombre) ya se encuentra dado de alta en el sistema")
                }else{
                print("Ingrese la edad del nuevo cliente: ")
                var edad=Int(readLine()!)!
                print("Ingrese el dinero a la cuenta del nuevo cliente: ")
                var dinero=Double(readLine()!)!
                print("Ingrese una contraseña para el cliente: ")
                var contraseña=readLine()!
                var cliente=Cliente(nombreCliente:nombre,
                                    edad:edad,
                                    dineroCuenta:dinero,
                                    password:contraseña)
                                    array.append(cliente)
                }
            }
            if(opcion==2){
                print("¿Esta seguro de que quiere eliminar permanentemente a este cliente?")
                print("1-Si 2-No")
                var decisión=readLine()!
                if decisión=="1"{
                print("Ingrese el número de identificación del cliente a eliminar (0 a \(array.count-1)):")
                if var eliminarcliente=Int(readLine()!),eliminarcliente>=0 && eliminarcliente < array.count{
                    array.remove(at:eliminarcliente)
                    print("Cliente eliminado exitosamente :).")
                    }else{
                    print("Número de identificación de cliente no válido")
                    } 
                }else{
                    print("Okey, entiendo.Tenga un buen día!")
                }
            }
            if(opcion==3){
                var banco=Banco()
                banco.verDatosBanco()
            }
            if(opcion==4){
                print("Ingrese el nuevo ID del banco: ")
                var nuevoID=readLine()!
                var banco=Banco()
                banco.setidBanco(idBanco:nuevoID)
            }
            if(opcion==5){
                print("Saliendo del Menú Administrador")
            }
       
        }while opcion != 5
    }
    if(opc==2){
        var opcionDOS=0 
        repeat{
            print("Menú Cliente")
            print("1-Mostrar datos personales del cliente")
            print("2-Mostrar dinero del cliente")
            print("3-Salir")
            opcionDOS=Int(readLine()!)!
            if(opcionDOS==1){
                print("Mostrando datos personales de clientes registrados:")
                print("Nombre: \(cliente.nombreCliente)")
                print("Edad: \(cliente.edad) años")
            }
            if(opcionDOS==2){
                print("Mostrando dinero en cuenta del cliente:")
                print("Dinero en cuenta: \(cliente.getDineroCuenta())")
            }
            if(opcionDOS==3){
                print("Saliendo del Menú Cliente")
            }
        }while opcionDOS != 3
    }
}while opc != 3
