//menu do crud

using System;
using System.ComponentModel;
using System.IO;
using System.Text;
using System.Threading.Tasks;
using static System.Runtime.InteropServices.JavaScript.JSType;
using gerenciador_de_estoque.utilitarios;

using gerenciador_de_estoque.src.Modelo;
using gerenciador_de_estoque.Servico;
using System.Collections.Generic;
using System.Linq;

InventarioServico.LoadAll();


static void CentralizarTexto(string texto)
{
    int larguraConsole = Console.WindowWidth;
    int espacos = Math.Max((larguraConsole - texto.Length) / 2, 0);
    Console.WriteLine(new string(' ', espacos) + texto);
}
static void CentralizarVertical(int linhasConteudo)
{
    int alturaConsole = Console.WindowHeight;
    int linhasEmBranco = Math.Max((alturaConsole - linhasConteudo) / 2, 0);
    for (int i = 0; i < linhasEmBranco; i++)
    {
        Console.WriteLine();
    }
}
static void senha(int sla)
{

    ConsoleKey tecla;
    int opcaoSenha = 0;
    bool teste = true;
    string pass = "1234";


    do
    {
        Console.Clear();
        CentralizarVertical(8);
        CentralizarTexto("            Digite a senha de acesso:            ");
        CentralizarTexto("                               ");
        CentralizarTexto(opcaoSenha == 0 ? "          >SIM<          " : "           SIM            ");
        CentralizarTexto(opcaoSenha == 1 ? "          >NÃO<          " : "           NÃO            ");
        CentralizarTexto("                               ");
        if (opcaoSenha == 0)
            CentralizarTexto("               Digitar senha                ");
        else
            CentralizarTexto("             Voltar para o menu                 ");
        tecla = Console.ReadKey(true).Key;
        if (tecla == ConsoleKey.UpArrow)
            opcaoSenha = (opcaoSenha - 1 + 2) % 2;
        else if (tecla == ConsoleKey.DownArrow)
            opcaoSenha = (opcaoSenha + 1) % 2;
        else if (tecla == ConsoleKey.Enter)
        {
            switch (opcaoSenha)
            {
                case 0:
                    Console.Write("Digite a senha de acesso: ");
                    string senhaa = Console.ReadLine();
                    switch (senhaa.Equals(pass))
                    {
                        case true:
                            teste = false;
                            Console.Clear();

                            if (sla == 0)
                            {
                                InventarioServico.ListarProdutos();
                                Console.ReadKey();
                            }
                            else if (sla == 1)
                            {
                                InventarioServico.CriarProduto();
                                Console.ReadKey();
                            }
                            else if (sla == 2)
                            {
                                InventarioServico.PesquisarProduto();
                                Console.ReadKey();
                            }
                            else if (sla == 3)
                            {
                                InventarioServico.SaveAll(); 
                                Console.ReadKey();
                            }
                            else if (sla == 4)
                            {
                                InventarioServico.Entrada();
                                Console.ReadKey();
                            }
                            else if (sla == 5)
                            {
                                InventarioServico.Saida();
                                Console.ReadKey();
                            }
                            else if (sla == 6)
                            {
                                InventarioServico.EditarProduto();
                                Console.ReadKey();
                            }
                            else if (sla == 7)
                            {
                                InventarioServico.ExcluirProduto();
                                Console.ReadKey();
                            }
                            else if (sla == 8)
                            {

                                Console.WriteLine("Histórico em desenvolvimento...");
                                Console.ReadKey();
                            }

                            break;


                            Console.ReadLine();
                            break;
                        case false:
                            Console.Clear();
                            Console.Write("Senha incorreta. Acesso negado.");
                            Console.ReadLine();
                            teste = true;
                            break;
                    }
                    break;
                case 1:
                    menuPrincipal();

                    break;
            }
        }
    } while (teste == true);
}


static void MenuSalvar()
{
    
    var produtos = CSVarmazenamento.ObterProdutos();
    CSVarmazenamento.SalvarProdutos();

    Console.WriteLine("\nDados salvos com sucesso!");
    Console.ReadKey();
    menuPrincipal();
}


static void MenuHist()
{
    do
    {

        CentralizarTexto("-----------------");
        CentralizarTexto("HIstorico de Alteração:");
        CentralizarTexto("fdsfsdfsfsdfsdfsd");
        CentralizarTexto("fdsfsdfsfsdfsdfsd");
        CentralizarTexto("fdsfsdfsfsdfsdfsd");
        break;
    } while (true);
}

static void menuPrincipal()
{
    bool condicao = true;
    ConsoleKey tecla;
    int opcaoMenu = 0;
    do
    {

        Console.Clear();
        CentralizarVertical(13);

        CentralizarTexto("         MENU DO ESTOQUE        ");
        CentralizarTexto("                                ");
        CentralizarTexto(opcaoMenu == 0 ? "      >LISTA DE CADASTROS<      " : "       LISTA DE CADASTROS       ");
        CentralizarTexto(opcaoMenu == 1 ? "          >CADASTRAR<           " : "           CADASTRAR            ");
        CentralizarTexto(opcaoMenu == 2 ? "           >BUSCAR<             " : "            BUSCAR              ");
        CentralizarTexto(opcaoMenu == 3 ? "           >SALVAR<             " : "            SALVAR              ");
        CentralizarTexto(opcaoMenu == 4 ? "          >ENTRADA<             " : "           ENTRADA              ");
        CentralizarTexto(opcaoMenu == 5 ? "           >SAIDA<              " : "            SAIDA               ");
        CentralizarTexto(opcaoMenu == 6 ? "       >EDITAR CADASTRO<        " : "        EDITAR CADASTRO         ");
        CentralizarTexto(opcaoMenu == 7 ? "      >EXCLUIR CADASTRO<        " : "       EXCLUIR CADASTRO         ");
        CentralizarTexto(opcaoMenu == 8 ? "   >HISTORICO DE ALTERAÇÕES<    " : "    HISTORICO DE ALTERAÇÕES     ");
        CentralizarTexto(opcaoMenu == 9 ? "        >SAIR DO MENU<          " : "         SAIR DO MENU           ");
        CentralizarTexto("                                ");

        if (opcaoMenu == 0)
        {
            CentralizarTexto("        >LISTA DE CADASTROS<      ");
        }
        else if (opcaoMenu == 1)
        {
            CentralizarTexto("           >CADASTRAR<            ");
        }
        else if (opcaoMenu == 2)
        {
            CentralizarTexto("             >BUSCAR<             ");
        }
        else if (opcaoMenu == 3)
        {
            CentralizarTexto("             >SALVAR<             ");
        }
        else if (opcaoMenu == 4)
        {
            CentralizarTexto("             >ENTRADA<            ");
        }
        else if (opcaoMenu == 5)
        {
            CentralizarTexto("               >SAIDA<            ");
        }
        else if (opcaoMenu == 6)
        {
            CentralizarTexto("         >EDITAR CADASTRO<        ");
        }
        else if (opcaoMenu == 7)
        {
            CentralizarTexto("        >EXCLUIR CADASTRO<        ");
        }
        else if (opcaoMenu == 8)
        {
            CentralizarTexto("    >HISTORICO DE ALTERAÇÕES<     ");
        }
        else if (opcaoMenu == 9)
        {
            CentralizarTexto("              >SAIR<              ");
        }

        tecla = Console.ReadKey(true).Key;

        if (tecla == ConsoleKey.UpArrow)
        {
            opcaoMenu = (opcaoMenu - 1 + 10) % 10;
        }
        else if (tecla == ConsoleKey.DownArrow)
        {
            opcaoMenu = (opcaoMenu + 1) % 10;
        }
        else if (tecla == ConsoleKey.Enter)
        {
            if(opcaoMenu == 0)
            {
                senha(opcaoMenu);
                Console.ReadKey();
            }
            if (opcaoMenu == 1)
            {
                senha(opcaoMenu);

                Console.ReadKey();
            }
            else if (opcaoMenu == 2)
            {
                senha(opcaoMenu);

                Console.ReadKey();
            }
            else if (opcaoMenu == 3)
            {
                senha(opcaoMenu);
                Console.ReadKey();
            }
            else if (opcaoMenu == 4)
            {
                senha(opcaoMenu);
            }
            else if (opcaoMenu == 5)
            {
                senha(opcaoMenu);
            }
            else if (opcaoMenu == 6)
            {
                senha(opcaoMenu);
                Console.ReadKey();
            }
            else if (opcaoMenu == 7)
            {
                senha(opcaoMenu);
                Console.ReadKey();
            }
            else if (opcaoMenu == 8)
            {
                senha(opcaoMenu);
                Console.WriteLine("Em desenvolvimento...");
                Console.ReadKey();
            }
            else if (opcaoMenu == 9)
            {
                MenuSair();
            }


        }
    } while (condicao == true);
}

static void MenuSair()
{
    ConsoleKey tecla;
    int opcaoSair = 0;
    bool condicao2 = true;
    do
    {
        Console.Clear();
        CentralizarVertical(7);
        CentralizarTexto("_______________II_______________");
        CentralizarTexto("          DESEJA SAIR?          ");
        CentralizarTexto("                                ");
        CentralizarTexto(opcaoSair == 0 ? "          >SIM<          " : "           SIM            ");
        CentralizarTexto(opcaoSair == 1 ? "          >NÃO<          " : "           NÃO            ");
        CentralizarTexto("_______________II_______________");
        if (opcaoSair == 0)
            CentralizarTexto("            >TCHAU<             ");
        else if (opcaoSair == 1)
            CentralizarTexto("             >UÉ<               ");
        tecla = Console.ReadKey(true).Key;
        if (tecla == ConsoleKey.UpArrow)
            opcaoSair = (opcaoSair - 1 + 2) % 2;
        else if (tecla == ConsoleKey.DownArrow)
            opcaoSair = (opcaoSair + 1) % 2;
        else if (tecla == ConsoleKey.Enter)
        {
            if (opcaoSair == 0)
            {
                Environment.Exit(0);
            }
            else if (opcaoSair == 1)
            {

                menuPrincipal();
            }
        }
    } while (condicao2 == true);
}

menuPrincipal();

//Ultilitarios

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace gerenciador_de_estoque.utilitarios
{
    public class Utilitarios
    {
        public int LerInt(string mensagem)
        {
            while (true)
            {
                Console.WriteLine(mensagem);
                if (int.TryParse(Console.ReadLine(), out int valor))
                    return valor;
                Console.WriteLine("Valor inválido! Digite um número inteiro.");
            }
        }
        public double LerDouble(string mensagem)
        {
            while (true)
            {
                Console.WriteLine(mensagem);
                if (double.TryParse(Console.ReadLine(), out double valor))
                    return valor;
                Console.WriteLine("Valor inválido! Digite um número válido.");
            }
        }
        public string LerTexto(string mensagem)
        {
            while (true)
            {
                Console.WriteLine(mensagem);
                string? input = Console.ReadLine();

                if (!string.IsNullOrWhiteSpace(input)) // verifica nulo, vazio ou só espaço
                    return input;

                Console.WriteLine("Valor inválido! Não pode ser vazio.");
            }
        }
        public static int MenuComSetas(string titulo, List<string> opcoes)
        {
            int selecionado = 0;
            ConsoleKey tecla;

            do
            {
                Console.Clear();
                Console.WriteLine(titulo + "\n");

                for (int i = 0; i < opcoes.Count; i++)
                {
                    if (i == selecionado)
                    {
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine($"> {opcoes[i]}");
                        Console.ResetColor();
                    }
                    else
                    {
                        Console.WriteLine($"  {opcoes[i]}");
                    }
                }

                tecla = Console.ReadKey(true).Key;

                if (tecla == ConsoleKey.UpArrow)
                {
                    selecionado--;
                    if (selecionado < 0)
                        selecionado = opcoes.Count - 1;
                }
                else if (tecla == ConsoleKey.DownArrow)
                {
                    selecionado++;
                    if (selecionado >= opcoes.Count)
                        selecionado = 0;
                }

            } while (tecla != ConsoleKey.Enter);

            return selecionado;
        }

    }
}

//Movimento

using gerenciador_de_estoque.utilitarios;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace gerenciador_de_estoque.src.Modelo
{
    public class Movimento
    {
        public record struct movimento(
            int Id,
            int ProdutoId,
            string Tipo,
            int Quantidade,
            DateTime Data,
            string Observacao
        );

        public static void Registrar(int id, int produtoId, string tipo, int quantidade, string observacao)
        {
            var data = DateTime.Now;
            string path = @"data\movimentos.csv";

            try
            {
                if (!Directory.Exists("data"))
                    Directory.CreateDirectory("data");

                if (!File.Exists(path))
                    File.WriteAllText(path, "id;produtoId;tipo;quantidade;data;observacao\n", Encoding.UTF8);

                string linha = $"{id};{produtoId};{tipo};{quantidade};{data:dd/MM/yyyy HH:mm};{observacao}\n";
                File.AppendAllText(path, linha, Encoding.UTF8);
            }
            catch (Exception ex)
            {
                Console.WriteLine($" Erro ao salvar movimento: {ex.Message}");
            }
        }
    }
}

//Lista de cadastro


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;

namespace gerenciador_de_estoque.src.Modelo
{
    public record struct Produto
    {
        public int Id { get; set; }
        public string Nome { get; set; }
        public string Categoria { get; set; }
        public int EstoqueMinimo { get; set; }
        public int Saldo { get; set; }


        public static void Listar(List<Produto> produtos)
        {
            if (produtos == null || produtos.Count == 0)
            {
                Console.WriteLine("\nNenhum produto cadastrado.");
                return;
            }

            Console.WriteLine("\nID | Nome               | Categoria        | Mínimo | Saldo");
            Console.WriteLine("---|--------------------|------------------|--------|------");

            foreach (var p in produtos)
            {
                Console.WriteLine(
                    $"{p.Id,2} | {p.Nome,-18} | {p.Categoria,-16} | {p.EstoqueMinimo,6} | {p.Saldo,5}"
                );
            }
        }


        public static void ExibirProdutosPorIDs(List<Produto> produtos, IEnumerable<int> idsDesejados)
        {
            if (produtos == null || produtos.Count == 0)
            {
                Console.WriteLine("\nNenhum produto cadastrado.");
                return;
            }

            var filtrados = produtos
                .Where(p => idsDesejados.Contains(p.Id))
                .ToList();

            if (filtrados.Count == 0)
            {
                Console.WriteLine("\nNenhum produto encontrado com os IDs informados.");
                return;
            }

            Console.WriteLine("\nID | Nome               | Categoria        | Mínimo | Saldo");
            Console.WriteLine("---|--------------------|------------------|--------|------");

            foreach (var p in filtrados)
            {
                Console.WriteLine(
                    $"{p.Id,2} | {p.Nome,-18} | {p.Categoria,-16} | {p.EstoqueMinimo,6} | {p.Saldo,5}"
                );
            }
        }
    }
}
